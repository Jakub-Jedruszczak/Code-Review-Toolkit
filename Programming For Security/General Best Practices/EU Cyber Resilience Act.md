# European Cyber Resilience Act (CRA)
The European Commission have estimated that the global annual cost of cybercrime will reach €5.5 trillion by 2021; the European Parliament proposed the European Cyber Resilience Act (CRA) in response to the rising success rate of cyber-attacks against software and hardware products.
Such products suffer from two major problems adding costs for users and the society:
1.	A low level of cybersecurity, reflected by widespread vulnerabilities and the insufficient and inconsistent provision of security updates to address them.
2.	An insufficient understanding and access to information by users, preventing them from choosing products with adequate cybersecurity properties or using them in a secure manner.
The Cyber Resilience Act addresses these issues by:
1.	Ensuring that manufacturers improve the security of products with digital elements since the design and development phase and throughout the whole life cycle.
2.	Ensuring a coherent cybersecurity framework, facilitating compliance for hardware and software producers.
3.	Enhancing the transparency of security properties of products with digital elements.
4.	Enabling businesses and consumers to use products with digital elements securely.
The CRA has been dubbed “the first Internet of Things legislation” as every internet-enabled device and almost every piece of software distributed in Europe will have to adhere to these regulations. Non-adherence comes with significant fines (€15 million or 2.5% of annual turnover, whichever is higher). Unlike the US National Cybersecurity Strategy or the UK’s Government Cyber Security Strategy, this legislation will impact every developer who distributes, imports or sells their software in Europe.
## Essential Acts
1.	_Products with digital elements shall be designed, developed and produced in such a way that they ensure an appropriate level of cybersecurity based on the risks;_ 
2.	_Products with digital elements shall be delivered without any known vulnerabilities_; do note that this means that a product will have to be immediately taken offline and off sale as soon as any vulnerability is discovered. This act will surely be revised in the future.
3.	a) _Products will be delivered with a secure by default configuration, including the possibility to reset the product to its original state_; essentially, “admin/admin” default logins are prohibited by law.
b) _Ensure protection from unauthorised access by appropriate control mechanisms, including but not limited to authentication, identity or access management systems;_
c) _Protect the confidentiality of stored, transmitted or otherwise processed data, personal or other, such as by encrypting relevant data at rest or in transit by state-of-the-art mechanisms;_
d) _Protect the integrity of stored, transmitted or otherwise processed data, personal or other, commands, programs and configuration against any manipulation or modification not authorised by the user, as well as report on corruptions;_
e) _Process only data, personal or other, that are adequate, relevant and limited to what is necessary in relation to the intended use of the product (‘minimisation of data’);_
f) _Protect the availability of essential functions, including the resilience against and mitigation of denial of service attacks;_ this item may be problematic as it forces all developers to make their services with (unspecified) denial of service attacks in mind, regardless of application.
h) _Be designed, developed and produced to limit attack surfaces, including external interfaces;_
k) _Ensure that vulnerabilities can be addressed through security updates, including, where applicable, through automatic updates and the notification of available updates to users._

## Behavioral Rules
1.	_Identify and document vulnerabilities and components contained in the product, including by drawing up a software bill of materials in a commonly used and machine-readable format covering at the very least the top-level dependencies of the product_;
2.	_In relation to the risks posed to the products with digital elements, address and remediate vulnerabilities without delay, including by providing security updates;_
3.	_Apply effective and regular tests and reviews of the security of the product with digital elements;_
4.	_Once a security update has been made available, publically disclose information about fixed vulnerabilities, including a description of the vulnerabilities, information allowing users to identify the product with digital elements affected, the impacts of the vulnerabilities, their severity and information helping users to remediate the vulnerabilities;_ essentially, developers have to be verbose about the vulnerabilities that have been patched, I.e. “various bug fixes” is not good enough.
5.	_Put in place and enforce a policy on coordinated vulnerability disclosure;_ vulnerability disclosure and possibly bug bounty programmes are now required
6.	_Take measures to facilitate the sharing of information about potential vulnerabilities in their product with digital elements as well as in third party components contained in that product, including by providing a contact address for the reporting of the vulnerabilities discovered in the product with digital elements;_ this item is designed to help track Common Vulnerabilities and Exposures, as well as to track supply chain attacks
7.	_Provide for mechanisms to securely distribute updates for products with digital elements to ensure that exploitable vulnerabilities are fixed or mitigated in a timely manner_; all network-enabled systems and subsystems must have the ability to receive patches
8.	_Ensure that, where security patches or updates are available to address identified security issues, they are disseminated without delay and free of charge, accompanied by advisory messages providing users with the relevant information, including on potential action to be taken._

## Further Reading

<https://digital-strategy.ec.europa.eu/en/library/cyber-resilience-act>
<https://www.europarl.europa.eu/thinktank/en/document/EPRS_BRI(2022)739259>
<https://berthub.eu/articles/posts/eu-cra-secure-coding-solution/>
