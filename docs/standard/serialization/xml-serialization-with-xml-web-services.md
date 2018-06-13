---
title: Serializace XML pomocí webové služby XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML Web services, XML serialization
- XML serialization, XML Web services
- SOAP, XML serialization
- asmx files
- serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- .asmx files
- encoded XML serialization
- literal XML serialization
- serialization, attributes
ms.assetid: a416192f-8102-458e-bc0a-0b8f3f784da9
ms.openlocfilehash: fdf984cd52441fd2bbe38499f981542386bd56ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591392"
---
# <a name="xml-serialization-with-xml-web-services"></a>Serializace XML pomocí webové služby XML
Serializace XML je základní přenos mechanismus použít v architektuře XML webových služeb, prováděné <xref:System.Xml.Serialization.XmlSerializer> třídy. K řízení XML generované webové služby XML, můžete použít atributy uvedené v obou [atributy, řízení XML serializace](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md) a [atributy, řízení kódovaný SOAP serializace](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md) do třídy, návratové hodnoty, parametry a pole souboru, který se používá k vytvoření webové služby XML (.asmx). Další informace o vytváření webové služby XML, najdete v části [vytváření XML webové služby pomocí ASP.NET](https://msdn.microsoft.com/library/01dfc27c-c68e-4910-a0aa-5e4c2a766b0c).  
  
## <a name="literal-and-encoded-styles"></a>Literál a kódovaného stylů  
 XML generované webové služby XML může být ve formátu v jedné ze dvou způsobů, buď literál nebo kódování, jak je popsáno v [přizpůsobení protokolu SOAP zprávy](https://msdn.microsoft.com/library/1d777288-c0d9-4e6a-b638-f010da031952). Proto existují dvě sady atributů, které řídí serializace XML. Atributy uvedené v [atributy, řízení XML serializace](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md) slouží k řízení literálu styl XML. Atributy uvedené v [atributy, řízení kódovaný SOAP serializace](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md) řízení kódovaného styl. Použitím selektivní tyto atributy, můžete přizpůsobit aplikace má být vrácena, obojím stylů. Kromě toho tyto atributy lze použít (v závislosti) má být vrácen hodnoty a parametry.  
  
### <a name="example-of-using-both-styles"></a>Příklad použití obou stylů  
 Při vytváření webové služby XML, můžete použít obě sady atributů pro metody. V následujícím příkladu kódu s názvem třídy `MyService` obsahuje dvě metody webové služby XML, `MyLiteralMethod` a `MyEncodedMethod`. Obě metody provádět má stejnou funkci: vrací instanci `Order` třídy. V `Order` třídy, <xref:System.Xml.Serialization.XmlTypeAttribute> a <xref:System.Xml.Serialization.SoapTypeAttribute> oba atributy jsou použity k `OrderID` pole a oba atributy mají jejich `ElementName` vlastností nastavenou na různé hodnoty.  
  
 Chcete-li spustit příklad, vložte kód do soubor s příponou .asmx a umístění souboru do virtuálního adresáře spravované Internet Information Services (IIS). Z prohlížeče, HTML, jako je například Internet Explorer zadejte název počítače, virtuální adresář a soubor.  
  
```vb  
<%@ WebService Language="VB" Class="MyService" %>  
Imports System  
Imports System.Web.Services  
Imports System.Web.Services.Protocols  
Imports System.Xml.Serialization  
Public Class Order  
    ' Both types of attributes can be applied. Depending on which type  
    ' the method used, either one will affect the call.  
    <SoapElement(ElementName:= "EncodedOrderID"), _  
    XmlElement(ElementName:= "LiteralOrderID")> _  
    public OrderID As String  
End Class  
  
Public Class MyService  
    <WebMethod, SoapDocumentMethod> _  
    public Function MyLiteralMethod() As Order   
        Dim myOrder As Order = New Order()  
        return myOrder  
    End Function  
    <WebMethod, SoapRpcMethod> _  
    public Function MyEncodedMethod() As Order   
        Dim myOrder As Order = New Order()  
        return myOrder  
    End Function  
End Class  
```  
  
```csharp  
<%@ WebService Language="C#" Class="MyService" %>  
using System;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using System.Xml.Serialization;  
public class Order{  
    // Both types of attributes can be applied. Depending on which type  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
public class MyService{  
    [WebMethod][SoapDocumentMethod]  
    public Order MyLiteralMethod(){  
        Order myOrder = new Order();  
        return myOrder;  
    }  
    [WebMethod][SoapRpcMethod]  
    public Order MyEncodedMethod(){  
        Order myOrder = new Order();  
        return myOrder;  
    }  
}  
```  
  
 Následující příklad volá kódu `MyLiteralMethod`. Název elementu se změní na "LiteralOrderID".  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethodResponse xmlns="http://tempuri.org/">  
            <MyLiteralMethodResult>  
                <LiteralOrderID>string</LiteralOrderID>  
            </MyLiteralMethodResult>  
        </MyLiteralMethodResponse>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 Následující příklad volá kódu `MyEncodedMethod`. Název elementu je "EncodedOrderID".  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:tns="http://tempuri.org/" xmlns:types="http://tempuri.org/encodedTypes" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body soap:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
        <tns:MyEncodedMethodResponse>  
            <MyEncodedMethodResult href="#id1" />  
        </tns:MyEncodedMethodResponse>  
        <types:Order id="id1" xsi:type="types:Order">  
            <EncodedOrderID xsi:type="xsd:string">string</EncodedOrderID>  
        </types:Order>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### <a name="applying-attributes-to-return-values"></a>Použití atributů vracet hodnoty  
 Můžete také použít atributy se mají vrátit hodnoty, které chcete určit obor názvů, název elementu a tak dále. Následující příklad kódu se vztahuje `XmlElementAttribute` atribut návratovou hodnotu `MyLiteralMethod` metody. To vám umožní název oboru názvů a elementu ovládacího prvku.  
  
```vb  
<WebMethod, SoapDocumentMethod> _  
public Function MyLiteralMethod() As _  
<XmlElement(Namespace:="http://www.cohowinery.com", _  
ElementName:= "BookOrder")> _  
Order   
    Dim myOrder As Order = New Order()  
    return myOrder  
End Function  
```  
  
```csharp  
[return: XmlElement(Namespace = "http://www.cohowinery.com",  
ElementName = "BookOrder")]  
[WebMethod][SoapDocumentMethod]  
public Order MyLiteralMethod(){  
    Order myOrder = new Order();  
    return myOrder;  
}  
```  
  
 Při vyvolání, vrátí kód XML, který se podobá níže.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethodResponse xmlns="http://tempuri.org/">  
            <BookOrder xmlns="http://www.cohowinery.com">  
                <LiteralOrderID>string</LiteralOrderID>  
            </BookOrder>  
        </MyLiteralMethodResponse>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### <a name="attributes-applied-to-parameters"></a>Atributy použité na parametry  
 Můžete také použít atributy k parametrům Chcete-li určit obor názvů, název elementu a tak dále. Následující příklad kódu přidá parametr, aby `MyLiteralMethodResponse` v případě metody a použije `XmlAttributeAttribute` atribut parametru. Název elementu a obor názvů jsou obě sady pro parametr.  
  
```vb  
<WebMethod, SoapDocumentMethod> _  
public Function MyLiteralMethod(<XmlElement _  
("MyOrderID", Namespace:="http://www.microsoft.com")>ID As String) As _  
<XmlElement(Namespace:="http://www.cohowinery.com", _  
ElementName:= "BookOrder")> _  
Order   
    Dim myOrder As Order = New Order()  
    myOrder.OrderID = ID  
    return myOrder  
End Function  
```  
  
```csharp  
[return: XmlElement(Namespace = "http://www.cohowinery.com",  
ElementName = "BookOrder")]  
[WebMethod][SoapDocumentMethod]  
public Order MyLiteralMethod([XmlElement("MyOrderID",   
Namespace="http://www.microsoft.com")] string ID){  
    Order myOrder = new Order();  
    myOrder.OrderID = ID;  
    return myOrder;  
}   
```  
  
 Požadavek SOAP bude vypadat takto.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethod xmlns="http://tempuri.org/">  
            <MyOrderID xmlns="http://www.microsoft.com">string</MyOrderID>  
        </MyLiteralMethod>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### <a name="applying-attributes-to-classes"></a>Použití atributů na třídy  
 Pokud je nutné určit obor názvů elementů, které se vztahují na třídy, můžete použít `XmlTypeAttribute`, `XmlRootAttribute`, a `SoapTypeAttribute`v případě potřeby. Následující příklad kódu se vztahuje na všechny tři `Order` třídy.  
  
```vb  
<XmlType("BigBookService"), _  
SoapType("SoapBookService"), _  
XmlRoot("BookOrderForm")> _  
Public Class Order  
    ' Both types of attributes can be applied. Depending on which  
    ' the method used, either one will affect the call.  
    <SoapElement(ElementName:= "EncodedOrderID"), _  
    XmlElement(ElementName:= "LiteralOrderID")> _  
    public OrderID As String  
End Class  
```  
  
```csharp  
[XmlType("BigBooksService", Namespace = "http://www.cpandl.com")]  
[SoapType("SoapBookService")]  
[XmlRoot("BookOrderForm")]  
public class Order{  
    // Both types of attributes can be applied. Depending on which  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
```  
  
 Výsledky používání `XmlTypeAttribute` a `SoapTypeAttribute` si můžete prohlédnout při kontrole popisu služby, jak je znázorněno v následujícím příkladu kódu.  
  
```xml  
    <s:element name="BookOrderForm" type="s0:BigBookService" />   
- <s:complexType name="BigBookService">  
- <s:sequence>  
    <s:element minOccurs="0" maxOccurs="1" name="LiteralOrderID" type="s:string" />   
    </s:sequence>  
  
- <s:schema targetNamespace="http://tempuri.org/encodedTypes">  
- <s:complexType name="SoapBookService">  
- <s:sequence>  
    <s:element minOccurs="1" maxOccurs="1" name="EncodedOrderID" type="s:string" />   
    </s:sequence>  
    </s:complexType>  
    </s:schema>  
```  
  
 Vliv `XmlRootAttribute` můžete také prohlédnout ve výsledcích HTTP GET a POST protokolu HTTP následujícím způsobem.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<BookOrderForm xmlns="http://tempuri.org/">  
    <LiteralOrderID>string</LiteralOrderID>  
</BookOrderForm>  
```  
  
## <a name="see-also"></a>Viz také  
 [Serializace XML a SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [Seznam atributů řídících serializaci zakódovanou v protokolu SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 [Postupy: Serializace objektu jako XML streamu zakódovaného v protokolu SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [Postupy: Přepsání serializace XML zakódované v protokolu SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [Představení serializace XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [Postupy: Serializace objektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Postupy: Deserializace objektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
