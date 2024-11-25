\<?xml version="1.0" encoding="UTF-8"?\>  
\<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"\>  
    \<xs:element name="services"\>  
        \<xs:complexType\>  
            \<xs:sequence\>  
                \<xs:element name="service" maxOccurs="unbounded"\>  
                    \<xs:complexType\>  
                        \<xs:sequence\>  
                            \<xs:element name="name" type="xs:string"/\>  
                            \<xs:element name="description" type="xs:string"/\>  
                            \<xs:element name="price" type="xs:decimal"/\>  
                            \<xs:element name="duration" type="xs:string"/\>  
                        \</xs:sequence\>  
                    \</xs:complexType\>  
                \</xs:element\>  
            \</xs:sequence\>  
        \</xs:complexType\>  
    \</xs:element\>  
\</xs:schema\>

