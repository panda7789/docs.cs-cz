---
title: Vytvoření vlastní hlavičky, která je podepsaná a/nebo šifrovaná
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: 0adb4100bca1add2c23ff2c802ddb5e2cb1c368c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579655"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a>Vytvoření vlastní hlavičky, která je podepsaná a/nebo šifrovaná
Při volání služby jiného typu než WCF pomocí klienta WCF je někdy nutné použít vlastní hlavičky SOAP. V rámci WCF existuje chyba kanonikalizace, která zabraňuje vlastním hlavičkám, které jsou podepsané a šifrované pro práci se službou jiného typu než WCF. Problém je způsoben nesprávnou kanonikalizací výchozích oborů názvů XML. To je problematické jenom při volání služeb jiných než WCF s vlastními hlavičkami, které jsou podepsané nebo šifrované.  Když služba obdrží zprávu obsahující podepsané a/nebo zašifrované vlastní záhlaví, nemůže ověřit podpis. Toto alternativní řešení předchází chybě kanonikalizace, umožňuje vzájemnou spolupráci s jinými službami než WCF, ale nebrání interoperabilitě se službami WCF.  
  
## <a name="defining-the-custom-header"></a>Definování vlastní hlavičky  
 Vlastní hlavičky jsou definovány definováním kontraktu zprávy a označením členů, které chcete odeslat jako záhlaví s <xref:System.ServiceModel.MessageHeaderAttribute> atributem. Chcete-li vyřešit chybu kanonikalizace, je nutné zajistit, aby serializátor XML deklaruje obor názvů pro vlastní hlavičku s předponou namísto výchozí deklarace oboru názvů. Následující kód ukazuje, jak definovat datový typ, který bude použit jako záhlaví zprávy se správnou deklarací oboru názvů.  
  
```csharp
[System.CodeDom.Compiler.GeneratedCodeAttribute("svcutil", "3.0.4506.648")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://www.example.org/getMessage/")]  
public partial class msgHeaderElement  
{  
   // Define the XML namespace and force it to use an ‘h’ prefix  
    [System.Xml.Serialization.XmlNamespaceDeclarations]  
    public System.Xml.Serialization.XmlSerializerNamespaces _xsns = new System.Xml.Serialization.XmlSerializerNamespaces(new System.Xml.XmlQualifiedName[] { new System.Xml.XmlQualifiedName("h", "http://www.example.org/getMessage/") });  
  
    private string msgHeaderInputField;  
  [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified, Order=0)]  
    public string msgHeaderInput  
    {  
        get  
        {  
            return this.msgHeaderInputField;  
        }  
        set  
        {  
            this.msgHeaderInputField = value;  
        }  
    }  
}  
```  
  
 Tento kód deklaruje nový typ s názvem `msgHeaderElement` , který bude serializován pomocí serializátoru XML. Když je serializována instance tohoto typu, definuje obor názvů s předponou "h", takže bude pracovat kolem chyby kanonikalizace.  Kontrakt zprávy by pak definoval instanci `msgHeaderElement` a označil ji <xref:System.ServiceModel.MessageHeaderAttribute> atributem, jak je znázorněno v následujícím příkladu.  
  
```csharp
[MessageContract]  
public  class MyMessageContract  
{  
   // other message contents...  
   [MessageHeader(ProductionLevel=ProtectionLevel.EncryptAndSign)]  
   public msgHeaderElement;  
   // other message contents...  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Výchozí kontrakt zprávy](../samples/default-message-contract.md)
- [Kontrakty zpráv](../samples/message-contracts.md)
- [Použití kontraktů zpráv](using-message-contracts.md)
