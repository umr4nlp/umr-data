# Contributing to UMR 2.0 Data

Thank you for your interest in improving the UMR 2.0 dataset! We welcome contributions from the community to help identify and fix errors in the annotations.

## How to Report Errors

If you find errors in the UMR annotations, you can contribute in two ways:

### 1. Create an Issue

For small numbers of errors or to discuss potential issues:

1. Go to the [Issues page](https://github.com/umr4nlp/umr-data/issues)
2. Click "New Issue"
3. Provide:
   - File name (e.g., `english/umr_data/english_umr-0001.umr`)
   - Sentence ID or block number
   - Description of the error
   - Proposed correction (if applicable)

### 2. Submit a Pull Request

For larger contributions or systematic fixes:

1. **Fork the repository**
   ```bash
   # Click the "Fork" button on GitHub
   ```

2. **Clone your fork**
   ```bash
   git clone https://github.com/YOUR_USERNAME/umr-data.git
   cd umr-data
   ```

3. **Create a new branch**
   ```bash
   git checkout -b fix/description-of-fix
   ```

4. **Make your corrections**
   - Edit the relevant `.umr` files in the language directories
   - Ensure you maintain the file format (see README.md for format description)
   - Test that the file can still parsed with [validation.py](https://github.com/ufal/UMR/blob/main/tools/validate.py)

5. **Commit your changes**
   ```bash
   git add .
   git commit -m "Fix: description of corrections"
   ```

6. **Push to your fork**
   ```bash
   git push origin fix/description-of-fix
   ```

7. **Create a Pull Request**
   - Go to the original repository on GitHub
   - Click "New Pull Request"
   - Select your branch
   - Describe your corrections in detail


## Questions?

If you have questions about:
- The UMR annotation format, see the [README.md](README.md)
- The UMR annotation guidelines, visit [umr-guidelines](https://github.com/umr4nlp/umr-guidelines)
- Contributing process, feel free to open an issue with your question


## License

By contributing, you agree that your contributions will be licensed under the same license as the original dataset.
