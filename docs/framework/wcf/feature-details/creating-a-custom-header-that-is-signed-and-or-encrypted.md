---
title: "Vytvoření vlastní hlavičky, která je podepsaná a- nebo šifrovaná"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b0faa62d75c506fd93c17c6a67aaecdd22bc8c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a><span data-ttu-id="7e7ed-102">Vytvoření vlastní hlavičky, která je podepsaná a- nebo šifrovaná</span><span class="sxs-lookup"><span data-stu-id="7e7ed-102">Creating a custom header that is signed and-or encrypted</span></span>
<span data-ttu-id="7e7ed-103">Při volání služby bez WCF pomocí klienta WCF je někdy nutné použít vlastní hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="7e7ed-103">When calling a non-WCF service using a WCF client it is sometimes necessary to use custom SOAP headers.</span></span> <span data-ttu-id="7e7ed-104">Ve službě WCF, který brání vlastní hlavičky, které jsou podepsat a zašifrovat práce služby bez WCF je kanonizace chyba.</span><span class="sxs-lookup"><span data-stu-id="7e7ed-104">There is a canonicalization bug in WCF that prevents custom headers that are signed and encrypted from working with a non-WCF service.</span></span> <span data-ttu-id="7e7ed-105">Problém je způsoben nesprávnou interpretaci výchozí obory názvů XML.</span><span class="sxs-lookup"><span data-stu-id="7e7ed-105">The problem is caused by the incorrect canonicalization of default XML namespaces.</span></span> <span data-ttu-id="7e7ed-106">Toto je pouze problematické, pokud volání služby bez WCF s vlastní hlavičky, které jsou podepsané a/nebo šifrovaná.</span><span class="sxs-lookup"><span data-stu-id="7e7ed-106">This is only problematic when calling non-WCF services with custom headers that are signed and/or encrypted.</span></span>  <span data-ttu-id="7e7ed-107">Když služba obdrží zprávu obsahující podepsaný držitelem nebo šifrované Vlastní hlavička se nepodařilo ověřit podpis.</span><span class="sxs-lookup"><span data-stu-id="7e7ed-107">When the service receives the message containing the signed and/or encrypted custom header it is unable to verify the signature.</span></span> <span data-ttu-id="7e7ed-108">Toto řešení zabraňuje kanonizace chyb, umožňuje vzájemnou spolupráci s služby bez WCF, ale nezabrání vzájemná funkční spolupráce s služby WCF.</span><span class="sxs-lookup"><span data-stu-id="7e7ed-108">This workaround avoids the canonicalization bug, allows interoperability with non-WCF services, but does not prevent interoperability with WCF services.</span></span>  
  
## <a name="defining-the-custom-header"></a><span data-ttu-id="7e7ed-109">Definování vlastní hlavičky</span><span class="sxs-lookup"><span data-stu-id="7e7ed-109">Defining the custom header</span></span>  
 <span data-ttu-id="7e7ed-110">Definováním kontrakt zprávy jsou definovány vlastní hlavičky a označení členů, které chcete odeslat jako záhlaví s <xref:System.ServiceModel.MessageHeaderAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="7e7ed-110">Custom headers are defined by defining a message contract and marking the members you want to be sent as headers with a <xref:System.ServiceModel.MessageHeaderAttribute> attribute.</span></span> <span data-ttu-id="7e7ed-111">Chcete-li vyřešit chyby kanonizace je nutné zajistit, že serializátor XML deklaruje obor názvů pro vlastní hlavičku s předponou místo výchozí deklaraci oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7e7ed-111">To work around the canonicalization bug you must ensure that the XML serializer declares the namespace for the custom header with a prefix instead of a default namespace declaration.</span></span> <span data-ttu-id="7e7ed-112">Následující kód ukazuje, jak k definování typu dat, který se použije jako záhlaví zprávy s deklaraci správný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="7e7ed-112">The following code shows how to define the data type that will be used as a message header with the correct namespace declaration.</span></span>  
  
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
  
 <span data-ttu-id="7e7ed-113">Tento kód deklaruje nového typu s názvem `msgHeaderElement` , se Dal serializovat s příznakem serializátoru XML.</span><span class="sxs-lookup"><span data-stu-id="7e7ed-113">This code declares a new type called `msgHeaderElement` that will be serialized with the XML Serializer.</span></span> <span data-ttu-id="7e7ed-114">Pokud instance tohoto typu je serializováno, ji budou definovat v oboru názvů s předponu "h", proto práce kolem kanonizace chyb.</span><span class="sxs-lookup"><span data-stu-id="7e7ed-114">When an instance of this type is serialized, it will define a namespace with an ‘h’ prefix, thus working around the canonicalization bug.</span></span>  <span data-ttu-id="7e7ed-115">Kontrakt zprávy by pak definovat instanci `msgHeaderElement` a označte ji s <xref:System.ServiceModel.MessageHeaderAttribute> atributu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7e7ed-115">The message contract would then define an instance of `msgHeaderElement` and mark it with the <xref:System.ServiceModel.MessageHeaderAttribute> attribute as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e7ed-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e7ed-116">See Also</span></span>  
 [<span data-ttu-id="7e7ed-117">Výchozí kontrakt zprávy</span><span class="sxs-lookup"><span data-stu-id="7e7ed-117">Default Message Contract</span></span>](../../../../docs/framework/wcf/samples/default-message-contract.md)  
 [<span data-ttu-id="7e7ed-118">Kontrakty zpráv</span><span class="sxs-lookup"><span data-stu-id="7e7ed-118">Message Contracts</span></span>](../../../../docs/framework/wcf/samples/message-contracts.md)  
 [<span data-ttu-id="7e7ed-119">Použití kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="7e7ed-119">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
