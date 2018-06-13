---
title: Vytvoření vlastní hlavičky, která je podepsaná a- nebo šifrovaná
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: 4770d650cba5c182aa56d9ac7afa39e585512d4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490692"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a>Vytvoření vlastní hlavičky, která je podepsaná a- nebo šifrovaná
Při volání služby bez WCF pomocí klienta WCF je někdy nutné použít vlastní hlavičky SOAP. Ve službě WCF, který brání vlastní hlavičky, které jsou podepsat a zašifrovat práce služby bez WCF je kanonizace chyba. Problém je způsoben nesprávnou interpretaci výchozí obory názvů XML. Toto je pouze problematické, pokud volání služby bez WCF s vlastní hlavičky, které jsou podepsané a/nebo šifrovaná.  Když služba obdrží zprávu obsahující podepsaný držitelem nebo šifrované Vlastní hlavička se nepodařilo ověřit podpis. Toto řešení zabraňuje kanonizace chyb, umožňuje vzájemnou spolupráci s služby bez WCF, ale nezabrání vzájemná funkční spolupráce s služby WCF.  
  
## <a name="defining-the-custom-header"></a>Definování vlastní hlavičky  
 Definováním kontrakt zprávy jsou definovány vlastní hlavičky a označení členů, které chcete odeslat jako záhlaví s <xref:System.ServiceModel.MessageHeaderAttribute> atribut. Chcete-li vyřešit chyby kanonizace je nutné zajistit, že serializátor XML deklaruje obor názvů pro vlastní hlavičku s předponou místo výchozí deklaraci oboru názvů. Následující kód ukazuje, jak k definování typu dat, který se použije jako záhlaví zprávy s deklaraci správný obor názvů.  
  
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
  
 Tento kód deklaruje nového typu s názvem `msgHeaderElement` , se Dal serializovat s příznakem serializátoru XML. Pokud instance tohoto typu je serializováno, ji budou definovat v oboru názvů s předponu "h", proto práce kolem kanonizace chyb.  Kontrakt zprávy by pak definovat instanci `msgHeaderElement` a označte ji s <xref:System.ServiceModel.MessageHeaderAttribute> atributu, jak je znázorněno v následujícím příkladu.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Výchozí kontrakt zprávy](../../../../docs/framework/wcf/samples/default-message-contract.md)  
 [Kontrakty zpráv](../../../../docs/framework/wcf/samples/message-contracts.md)  
 [Použití kontraktů zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
