---
title: Přidání odkazu služby v přenosném dílčím projektu
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: 5d094bb1d2d1155565e48850a2f41829a93cff84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460486"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="3533b-102">Přidání odkazu služby v přenosném dílčím projektu</span><span class="sxs-lookup"><span data-stu-id="3533b-102">Add Service Reference in a Portable Subset Project</span></span>
<span data-ttu-id="3533b-103">Projekty přenosném dílčím povolit programátorům sestavení .NET udržovat stromu jednoho zdroje a sestavení systému, přičemž musí zároveň podporovat více implementace rozhraní .NET (plochy, Silverlight, Windows Phone a XBOX).</span><span class="sxs-lookup"><span data-stu-id="3533b-103">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and XBOX).</span></span> <span data-ttu-id="3533b-104">Projekty přenosném dílčím odkazovat pouze na přenosné knihovny .NET, které jsou sestavení rozhraní .NET framework, který lze použít na žádnou implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3533b-104">Portable subset projects only reference .NET portable libraries which are a .NET framework assembly that can be used on any .NET implementation.</span></span>  
  
## <a name="add-service-reference-details"></a><span data-ttu-id="3533b-105">Přidat odkaz na podrobnosti služby</span><span class="sxs-lookup"><span data-stu-id="3533b-105">Add Service Reference Details</span></span>  
 <span data-ttu-id="3533b-106">Při přidání odkazu na službu v přenosném dílčím projektu se vynucují následující omezení:</span><span class="sxs-lookup"><span data-stu-id="3533b-106">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1.  <span data-ttu-id="3533b-107">Pro <xref:System.Xml.Serialization.XmlSerializer>, jsou povoleny pouze literál kódování.</span><span class="sxs-lookup"><span data-stu-id="3533b-107">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="3533b-108">Kódování SOAP k chybě při importu.</span><span class="sxs-lookup"><span data-stu-id="3533b-108">SOAP encodings generate an error during import.</span></span>  
  
2.  <span data-ttu-id="3533b-109">Pro služby, které používají <xref:System.Runtime.Serialization.DataContractSerializer> scénáře, data se zajistit, že znovu používané typy pocházejí pouze z přenosném dílčím poskytuje náhradní kontrakt.</span><span class="sxs-lookup"><span data-stu-id="3533b-109">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3.  <span data-ttu-id="3533b-110">Koncové body, které jsou závislé na vazby není podporována v přenosné knihovny (všechny vazby s výjimkou <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> bez toku transakcí, spolehlivé relace, nebo kódování MTOM a ekvivalentní vlastní vazby) se ignorují.</span><span class="sxs-lookup"><span data-stu-id="3533b-110">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4.  <span data-ttu-id="3533b-111">Hlavičky zpráv jsou odstraněny z všechny popisy zpráv ve všech operací před importem.</span><span class="sxs-lookup"><span data-stu-id="3533b-111">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5.  <span data-ttu-id="3533b-112">Atributy non přenositelností <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, a <xref:System.ServiceModel.TransactionFlowAttribute> se odeberou z kódu generovaného klienta proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="3533b-112">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6.  <span data-ttu-id="3533b-113">Bez přenositelností vlastnosti ProtectionLevel, SessionMode, IsInitiating, IsTerminating se odeberou z <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, a <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3533b-113">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7.  <span data-ttu-id="3533b-114">Všechny operace služby jsou generovány jako asynchronní operace na proxy serveru klienta.</span><span class="sxs-lookup"><span data-stu-id="3533b-114">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8.  <span data-ttu-id="3533b-115">Konstruktory generovaného klienta, které používají jiný přenositelností typy jsou odebrány.</span><span class="sxs-lookup"><span data-stu-id="3533b-115">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="3533b-116">A <xref:System.Net.CookieContainer> instance je vystaven na generovaného klienta.</span><span class="sxs-lookup"><span data-stu-id="3533b-116">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="3533b-117">V horní části souboru určíte sestavení a verze generátor kódu je vložit komentář:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="3533b-117">A comment is inserted at the top of the file identifying the assembly and version of the code generator:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span></span>  
  
11. <span data-ttu-id="3533b-118"><xref:System.Runtime.Serialization.ISerializable> Rozhraní není podporováno.</span><span class="sxs-lookup"><span data-stu-id="3533b-118">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="3533b-119">Vazby Net.Tcp a PollingDuplex nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="3533b-119">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="3533b-120"><xref:System.Runtime.Serialization.DataContractSerializer> Se vždycky použije pro chyb.</span><span class="sxs-lookup"><span data-stu-id="3533b-120">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <span data-ttu-id="3533b-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> není podporována v přenosném dílčím projekty.</span><span class="sxs-lookup"><span data-stu-id="3533b-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3533b-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="3533b-122">See Also</span></span>  
 [<span data-ttu-id="3533b-123">Přístup ke službám pomocí klienta WCF</span><span class="sxs-lookup"><span data-stu-id="3533b-123">Accessing Services Using a WCF Client</span></span>](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 <span data-ttu-id="3533b-124">[Přenosná knihovna tříd](http://msdn.microsoft.com/library/gg597391\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3533b-124">[Portable Class Library](http://msdn.microsoft.com/library/gg597391\(v=vs.110\))</span></span>
