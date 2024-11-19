# python-error-handling
def read_and_write_file():
    """
    Read a file and write a modified version to a new file, handling errors.
    """
    # Ask the user for the filename to read
    input_filename = input("Enter the filename to read from: ")

    try:
        # Attempt to open and read the file
        with open(input_filename, 'r') as infile:
            content = infile.readlines()

        # Modify the content (e.g., adding line numbers)
        modified_content = [f"{idx + 1}: {line}" for idx, line in enumerate(content)]

        # Write the modified content to a new file
        output_filename = "modified_" + input_filename
        with open(output_filename, 'w') as outfile:
            outfile.writelines(modified_content)

        print(f"Modified content has been written to {output_filename}")

    except FileNotFoundError:
        # Handle the case where the file does not exist
        print(f"Error: The file '{input_filename}' does not exist.")
    except IOError:
        # Handle other I/O errors (e.g., permissions issues)
        print(f"Error: The file '{input_filename}' could not be read or written.")

# Run the function
read_and_write_file()
