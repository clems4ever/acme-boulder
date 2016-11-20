# ACME Boulder

ACME Boulder will help deploy your own ACME boulder in minutes so that you can sign certificates as if you were letsencrypt. By the way, the boulder is the one used by letsencrypt that I tweaked and packaged.

## Quickstart

Everything is already packaged so that you deploy it very easily.
Before starting, make sure that you have vagrant and virtualbox installed on your computer.

    vagrant up
    vagrant provision
    
The last command sets up and provisions two VMs (their surnames are 'boulder' and 'issuer').
It may take few minutes before everything is set up (and even after ansible finished provisioning the VMs) but once everything is done, log into the issuer VM with the following command:
    
    vagrant ssh issuer
    
And try to issue a certificate with certbot which is already installed in the VM

    sudo certbot certonly -a standalone -d test.example.com --server http://192.168.2.200:4000/directory
    
And you should get your certificate right away. The trick is the --server flag that points to the boulder.

## Contributing to ACME Boulder

Follow [contributing](CONTRIBUTING.md) file.

## License

ACME Boulder is **licensed** under the **[MIT License]**. The terms of the license are as follows:

    The MIT License (MIT)

    Copyright (c) 2016 - Clement Michaud

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in
    all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
    WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
    CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


[MIT License]: https://opensource.org/licenses/MIT
