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
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a><span data-ttu-id="a7d46-102">Vytvoření vlastní hlavičky, která je podepsaná a/nebo šifrovaná</span><span class="sxs-lookup"><span data-stu-id="a7d46-102">Creating a custom header that is signed and-or encrypted</span></span>
<span data-ttu-id="a7d46-103">Při volání služby jiného typu než WCF pomocí klienta WCF je někdy nutné použít vlastní hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="a7d46-103">When calling a non-WCF service using a WCF client it is sometimes necessary to use custom SOAP headers.</span></span> <span data-ttu-id="a7d46-104">V rámci WCF existuje chyba kanonikalizace, která zabraňuje vlastním hlavičkám, které jsou podepsané a šifrované pro práci se službou jiného typu než WCF.</span><span class="sxs-lookup"><span data-stu-id="a7d46-104">There is a canonicalization bug in WCF that prevents custom headers that are signed and encrypted from working with a non-WCF service.</span></span> <span data-ttu-id="a7d46-105">Problém je způsoben nesprávnou kanonikalizací výchozích oborů názvů XML.</span><span class="sxs-lookup"><span data-stu-id="a7d46-105">The problem is caused by the incorrect canonicalization of default XML namespaces.</span></span> <span data-ttu-id="a7d46-106">To je problematické jenom při volání služeb jiných než WCF s vlastními hlavičkami, které jsou podepsané nebo šifrované.</span><span class="sxs-lookup"><span data-stu-id="a7d46-106">This is only problematic when calling non-WCF services with custom headers that are signed and/or encrypted.</span></span>  <span data-ttu-id="a7d46-107">Když služba obdrží zprávu obsahující podepsané a/nebo zašifrované vlastní záhlaví, nemůže ověřit podpis.</span><span class="sxs-lookup"><span data-stu-id="a7d46-107">When the service receives the message containing the signed and/or encrypted custom header it is unable to verify the signature.</span></span> <span data-ttu-id="a7d46-108">Toto alternativní řešení předchází chybě kanonikalizace, umožňuje vzájemnou spolupráci s jinými službami než WCF, ale nebrání interoperabilitě se službami WCF.</span><span class="sxs-lookup"><span data-stu-id="a7d46-108">This workaround avoids the canonicalization bug, allows interoperability with non-WCF services, but does not prevent interoperability with WCF services.</span></span>  
  
## <a name="defining-the-custom-header"></a><span data-ttu-id="a7d46-109">Definování vlastní hlavičky</span><span class="sxs-lookup"><span data-stu-id="a7d46-109">Defining the custom header</span></span>  
 <span data-ttu-id="a7d46-110">Vlastní hlavičky jsou definovány definováním kontraktu zprávy a označením členů, které chcete odeslat jako záhlaví s <xref:System.ServiceModel.MessageHeaderAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="a7d46-110">Custom headers are defined by defining a message contract and marking the members you want to be sent as headers with a <xref:System.ServiceModel.MessageHeaderAttribute> attribute.</span></span> <span data-ttu-id="a7d46-111">Chcete-li vyřešit chybu kanonikalizace, je nutné zajistit, aby serializátor XML deklaruje obor názvů pro vlastní hlavičku s předponou namísto výchozí deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a7d46-111">To work around the canonicalization bug you must ensure that the XML serializer declares the namespace for the custom header with a prefix instead of a default namespace declaration.</span></span> <span data-ttu-id="a7d46-112">Následující kód ukazuje, jak definovat datový typ, který bude použit jako záhlaví zprávy se správnou deklarací oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a7d46-112">The following code shows how to define the data type that will be used as a message header with the correct namespace declaration.</span></span>  
  
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
  
 <span data-ttu-id="a7d46-113">Tento kód deklaruje nový typ s názvem `msgHeaderElement` , který bude serializován pomocí serializátoru XML.</span><span class="sxs-lookup"><span data-stu-id="a7d46-113">This code declares a new type called `msgHeaderElement` that will be serialized with the XML Serializer.</span></span> <span data-ttu-id="a7d46-114">Když je serializována instance tohoto typu, definuje obor názvů s předponou "h", takže bude pracovat kolem chyby kanonikalizace.</span><span class="sxs-lookup"><span data-stu-id="a7d46-114">When an instance of this type is serialized, it will define a namespace with an ‘h’ prefix, thus working around the canonicalization bug.</span></span>  <span data-ttu-id="a7d46-115">Kontrakt zprávy by pak definoval instanci `msgHeaderElement` a označil ji <xref:System.ServiceModel.MessageHeaderAttribute> atributem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a7d46-115">The message contract would then define an instance of `msgHeaderElement` and mark it with the <xref:System.ServiceModel.MessageHeaderAttribute> attribute as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7d46-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7d46-116">See also</span></span>

- [<span data-ttu-id="a7d46-117">Výchozí kontrakt zprávy</span><span class="sxs-lookup"><span data-stu-id="a7d46-117">Default Message Contract</span></span>](../samples/default-message-contract.md)
- [<span data-ttu-id="a7d46-118">Kontrakty zpráv</span><span class="sxs-lookup"><span data-stu-id="a7d46-118">Message Contracts</span></span>](../samples/message-contracts.md)
- [<span data-ttu-id="a7d46-119">Použití kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="a7d46-119">Using Message Contracts</span></span>](using-message-contracts.md)
