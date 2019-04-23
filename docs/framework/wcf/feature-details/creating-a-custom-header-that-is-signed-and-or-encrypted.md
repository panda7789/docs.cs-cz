---
title: Vytvoření vlastní hlavičky, která je podepsaná a/nebo šifrovaná
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: 76bfb6040f6b78765ed42ce7fbf86cdbd62c1e48
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075625"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a>Vytvoření vlastní hlavičky, která je podepsaná a/nebo šifrovaná
Při volání služby typu bez WCF pomocí klienta WCF je někdy potřeba použít vlastní hlavičky SOAP. Ve službě WCF, který brání vlastní hlavičky, které jsou podepsány a šifrovány práci se službou bez WCF je Chyba převodu do kanonického tvaru. Problém je způsoben nesprávnou interpretaci výchozí obory názvů XML. Toto je pouze problematické při volání služby bez WCF s vlastní hlavičky, které jsou podepsané a/nebo šifrovaná.  Když služba přijímá zprávy obsahující podepsaný a/nebo šifrovaná vlastní hlavičky nelze ověřit podpis. Toto řešení se vyhnete chyby převodu do kanonického tvaru, umožňuje spolupráci se službami jiných WCF, ale nezabrání interoperabilita se službami WCF.  
  
## <a name="defining-the-custom-header"></a>Definování vlastní hlavičky  
 Vlastní hlavičky, které jsou definovány pomocí definování kontraktu zprávy a označení členů, které chcete odeslat jako záhlaví s <xref:System.ServiceModel.MessageHeaderAttribute> atribut. Chcete-li vyřešit chyby převodu do kanonického tvaru musíte zajistit, že serializátor XML deklaruje obor názvů pro vlastní záhlaví s předponou místo výchozí deklaraci oboru názvů. Následující kód ukazuje, jak definovat datový typ, který se použije jako záhlaví zprávy s deklarací správný obor názvů.  
  
```  
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
  
 Tento kód deklaruje nový typ s názvem `msgHeaderElement` , který by se Dal serializovat s příznakem serializátor XML. Pokud je serializována instance tohoto typu, ji budou definovat obor názvů s předponou "h", tedy obejít chyby převodu do kanonického tvaru.  Kontrakt zprávy potom definujte instance `msgHeaderElement` a označte ji pomocí <xref:System.ServiceModel.MessageHeaderAttribute> atributu, jak je znázorněno v následujícím příkladu.  
  
```  
[MessageContract]  
public  class MyMessageContract  
{  
   // other message contents...  
   [MessageHeader(ProductionLevel=ProtectionLevel.EncryptAndSign)]  
   public msgHeaderElement;  
   // other message contents...  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Výchozí kontrakt zprávy](../../../../docs/framework/wcf/samples/default-message-contract.md)
- [Kontrakty zpráv](../../../../docs/framework/wcf/samples/message-contracts.md)
- [Použití kontraktů zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
