---
title: Přidání odkazu služby v přenosném dílčím projektu
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: 764ce487d8f2673eb2c75f8cd05da4ccbae3c935
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320841"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="1214a-102">Přidání odkazu služby v přenosném dílčím projektu</span><span class="sxs-lookup"><span data-stu-id="1214a-102">Add Service Reference in a Portable Subset Project</span></span>
<span data-ttu-id="1214a-103">Přenositelné podmnožiny projektů umožňují programátorům sestavení .NET udržovat jeden zdrojový strom a systém sestavení a přitom stále podporovat více implementací .NET (Desktop, Silverlight, Windows Phone a XBOX).</span><span class="sxs-lookup"><span data-stu-id="1214a-103">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and XBOX).</span></span> <span data-ttu-id="1214a-104">Přenositelné Podmnožinové projekty odkazují pouze na přenosné knihovny .NET, které jsou sestavením rozhraní .NET Framework, které lze použít v jakékoli implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="1214a-104">Portable subset projects only reference .NET portable libraries which are a .NET framework assembly that can be used on any .NET implementation.</span></span>  
  
## <a name="add-service-reference-details"></a><span data-ttu-id="1214a-105">Podrobnosti Přidat odkaz na službu</span><span class="sxs-lookup"><span data-stu-id="1214a-105">Add Service Reference Details</span></span>  
 <span data-ttu-id="1214a-106">Při přidávání odkazu na službu v přenositelné podmnožině projektu se vynutila následující omezení:</span><span class="sxs-lookup"><span data-stu-id="1214a-106">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1. <span data-ttu-id="1214a-107">U <xref:System.Xml.Serialization.XmlSerializer> jsou povoleny pouze literální kódování.</span><span class="sxs-lookup"><span data-stu-id="1214a-107">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="1214a-108">Kódování SOAP generují chybu během importu.</span><span class="sxs-lookup"><span data-stu-id="1214a-108">SOAP encodings generate an error during import.</span></span>  
  
2. <span data-ttu-id="1214a-109">Pro služby, které používají scénáře <xref:System.Runtime.Serialization.DataContractSerializer>, je k dispozici náhrada kontraktu dat, která zajistí, že se znovu používané typy předávají jenom z přenosné podmnožiny.</span><span class="sxs-lookup"><span data-stu-id="1214a-109">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3. <span data-ttu-id="1214a-110">Koncové body, které spoléhají na vazby, nejsou v přenosných knihovnách podporovány (všechny vazby kromě <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> bez toku transakcí, spolehlivých relací nebo kódování MTOM a ekvivalentní vlastní vazby) se ignorují.</span><span class="sxs-lookup"><span data-stu-id="1214a-110">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4. <span data-ttu-id="1214a-111">Před importem se odstraní záhlaví zpráv ze všech popisů zpráv ve všech operacích.</span><span class="sxs-lookup"><span data-stu-id="1214a-111">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5. <span data-ttu-id="1214a-112">Nepřenosné atributy <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute> a <xref:System.ServiceModel.TransactionFlowAttribute> jsou odebrány z generovaného klientského proxy kódu.</span><span class="sxs-lookup"><span data-stu-id="1214a-112">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6. <span data-ttu-id="1214a-113">Nepřenosné vlastnosti ProtectionLevel, SessionMode, IsInitiating a IsTerminating se odeberou z <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute> a <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1214a-113">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7. <span data-ttu-id="1214a-114">Všechny operace služby jsou generovány jako asynchronní operace na klientském proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="1214a-114">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8. <span data-ttu-id="1214a-115">Vygenerované klientské konstruktory, které používají nepřenosné typy, se odeberou.</span><span class="sxs-lookup"><span data-stu-id="1214a-115">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="1214a-116">Na vygenerovaného klientovi je vystavená instance <xref:System.Net.CookieContainer>.</span><span class="sxs-lookup"><span data-stu-id="1214a-116">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="1214a-117">Komentář je vložen na začátek souboru, který identifikuje sestavení a verzi generátoru kódu: `// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="1214a-117">A comment is inserted at the top of the file identifying the assembly and version of the code generator:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span></span>  
  
11. <span data-ttu-id="1214a-118">Rozhraní <xref:System.Runtime.Serialization.ISerializable> se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="1214a-118">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="1214a-119">Vazby NET. TCP a PollingDuplex se nepodporují.</span><span class="sxs-lookup"><span data-stu-id="1214a-119">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="1214a-120">@No__t-0 bude vždy použito pro chyby.</span><span class="sxs-lookup"><span data-stu-id="1214a-120">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <span data-ttu-id="1214a-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> není v přenosných podmnožinách projektů podporováno.</span><span class="sxs-lookup"><span data-stu-id="1214a-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1214a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1214a-122">See also</span></span>

- [<span data-ttu-id="1214a-123">Přístup ke službám pomocí klienta WCF</span><span class="sxs-lookup"><span data-stu-id="1214a-123">Accessing Services Using a WCF Client</span></span>](accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="1214a-124">Přenosná knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="1214a-124">Portable Class Library</span></span>](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
