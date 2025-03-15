#!/usr/bin/env python3

import yaml
import xml.etree.ElementTree as ET
from xml.dom import minidom
import argparse


def convert_vcs_to_manifest(vcs_file, output_file):
    """Convert vcs repos file to repo manifest xml file"""

    # Read vcs file
    with open(vcs_file, "r") as f:
        vcs_data = yaml.safe_load(f)

    # Create manifest root
    manifest = ET.Element("manifest")

    # Add remote
    remote = ET.SubElement(manifest, "remote")
    remote.set("name", "github")
    remote.set("fetch", "https://github.com")

    # Add default
    default = ET.SubElement(manifest, "default")
    default.set("revision", "rolling")
    default.set("remote", "github")
    default.set("sync-j", "4")

    # Process each repository
    for repo_path, repo_info in vcs_data["repositories"].items():
        project = ET.SubElement(manifest, "project")

        # Extract repo name from url
        url = repo_info["url"]
        repo_name = url.replace("https://github.com/", "")

        # Set project attributes
        project.set("path", repo_path)
        project.set("name", repo_name)

        # Set revision if not rolling
        if repo_info["version"] != "rolling":
            project.set("revision", repo_info["version"])

    # Pretty print XML
    xml_str = minidom.parseString(ET.tostring(manifest)).toprettyxml(indent="  ")

    # Write to file
    with open(output_file, "w") as f:
        f.write(xml_str)


def main():
    parser = argparse.ArgumentParser(description="Convert vcs repos file to repo manifest")
    parser.add_argument("input", help="Input vcs repos file")
    parser.add_argument(
        "-o", "--output", default="default.xml", help="Output manifest file (default: default.xml)"
    )

    args = parser.parse_args()

    try:
        convert_vcs_to_manifest(args.input, args.output)
        print(f"Successfully converted {args.input} to {args.output}")
    except Exception as e:
        print(f"Error converting file: {e}")


if __name__ == "__main__":
    main()
