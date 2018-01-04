---
title: "Zmírnění: Deserializace objektů mezi doménami aplikací"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa156c914d2a1bb2ff0601d9e06c9b87d4190754
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a><span data-ttu-id="df74b-102">Zmírnění: Deserializace objektů mezi doménami aplikací</span><span class="sxs-lookup"><span data-stu-id="df74b-102">Mitigation: Deserialization of Objects Across App Domains</span></span>
<span data-ttu-id="df74b-103">V některých případech, kdy aplikace používá dvě nebo více domén aplikace s různými základy cesty aplikace, vyvolá pokus o deserializaci objektů v rámci logického kontextu volání mezi doménami aplikace výjimku.</span><span class="sxs-lookup"><span data-stu-id="df74b-103">In some cases, when an app uses two or more app domains with different application bases, the attempt to deserialize objects in the logical call context across app domains throws an exception.</span></span>  
  
## <a name="diagnosing-the-issue"></a><span data-ttu-id="df74b-104">Diagnostika problému</span><span class="sxs-lookup"><span data-stu-id="df74b-104">Diagnosing the issue</span></span>  
 <span data-ttu-id="df74b-105">Tento problém nastane při následující posloupnosti podmínek:</span><span class="sxs-lookup"><span data-stu-id="df74b-105">The issue arises under the following sequence of conditions:</span></span>  
  
1.  <span data-ttu-id="df74b-106">Aplikace používá dvě nebo více domén aplikace s různými základy cesty aplikace.</span><span class="sxs-lookup"><span data-stu-id="df74b-106">An app uses two or more app domains with different application bases.</span></span>  
  
2.  <span data-ttu-id="df74b-107">Některé typy jsou explicitně přidány do typu <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> voláním metody, jako je <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> nebo <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="df74b-107">Some types are explicitly added to the <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> by calling a method such as <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> or <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="df74b-108">Tyto typy nejsou označeny jako serializovatelné a nejsou uloženy v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="df74b-108">These types are not marked as serializable and are not stored in the global assembly cache.</span></span>  
  
3.  <span data-ttu-id="df74b-109">Později se kód spuštěný v jiné doméně aplikace, než je výchozí doména, pokusí načíst hodnotu z konfiguračního souboru, nebo pomocí jazyka XML deserializuje objekt.</span><span class="sxs-lookup"><span data-stu-id="df74b-109">Later, code running in the non-default app domain tries to read a value from a configuration file or use XML to deserialize an object.</span></span>  
  
4.  <span data-ttu-id="df74b-110">Aby proběhlo načtení z konfiguračního souboru nebo deserializace objektu, pokusí se objekt <xref:System.Xml.XmlReader> o přístup k systému konfigurace.</span><span class="sxs-lookup"><span data-stu-id="df74b-110">In order to read from a configuration file or deserialize the object, an <xref:System.Xml.XmlReader> object tries to access the configuration system.</span></span>  
  
5.  <span data-ttu-id="df74b-111">Pokud systém konfigurace ještě nebyl inicializován, je nutné dokončit jeho inicializaci.</span><span class="sxs-lookup"><span data-stu-id="df74b-111">If the configuration system has not already been initialized, it must complete its initialization.</span></span> <span data-ttu-id="df74b-112">Mimo jiné to znamená, že modul runtime musí vytvořit stabilní cestu pro systém konfigurace, což se provádí takto:</span><span class="sxs-lookup"><span data-stu-id="df74b-112">This means, among other things, that the runtime has to create a stable path for a configuration system, which it does as follows:</span></span>  
  
    1.  <span data-ttu-id="df74b-113">Hledá legitimaci nevýchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="df74b-113">It looks for evidence for the non-default app domain.</span></span>  
  
    2.  <span data-ttu-id="df74b-114">Pokusí se vypočítat legitimaci nevýchozí domény aplikace založené na výchozí doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="df74b-114">It tries to calculate the evidence for the non-default app domain based on the default app domain.</span></span>  
  
    3.  <span data-ttu-id="df74b-115">Volání uskutečněné za účelem získání legitimace výchozí domény aplikace spustí volání napříč doménou aplikace z nevýchozí domény aplikace do výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="df74b-115">The call to get evidence for the default app domain triggers a cross-app domain call from the non-default app domain to the default app domain.</span></span>  
  
    4.  <span data-ttu-id="df74b-116">Jako součást kontraktu napříč doménami aplikace v rozhraní .NET Framework musí být obsah logického kontextu volání zařazen napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="df74b-116">As part of the cross-app domain contract in the .NET Framework, the contents of the logical call context also have to be marshaled across app domain boundaries.</span></span>  
  
6.  <span data-ttu-id="df74b-117">Vzhledem k tomu, že ve výchozí doméně aplikace nelze rozpoznat typy, které jsou součástí logického kontextu volání, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="df74b-117">Because the types that are in the logical call context cannot be resolved in the default app domain, an exception is thrown.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="df74b-118">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="df74b-118">Mitigation</span></span>  
 <span data-ttu-id="df74b-119">Chcete-li tento problém odstranit, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="df74b-119">To work around this issue, do the following</span></span>  
  
1.  <span data-ttu-id="df74b-120">Pokud je vyvolána výjimka, v zásobníku volání vyhledejte volání metody `get_Evidence`.</span><span class="sxs-lookup"><span data-stu-id="df74b-120">Look for the call to `get_Evidence` in the call stack when the exception is thrown.</span></span> <span data-ttu-id="df74b-121">Touto výjimkou může být jakkoli velká podmnožina výjimek, včetně výjimek <xref:System.IO.FileNotFoundException> a <xref:System.Runtime.Serialization.SerializationException>.</span><span class="sxs-lookup"><span data-stu-id="df74b-121">The exception can be any of a large subset of exceptions, including <xref:System.IO.FileNotFoundException> and <xref:System.Runtime.Serialization.SerializationException>.</span></span>  
  
2.  <span data-ttu-id="df74b-122">Určete místo v aplikaci, ve kterém nejsou do logického kontextu volání přidány žádné objekty, a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="df74b-122">Identify the place in the app where no objects are added to the logical call context and add the following code:</span></span>  
  
    ```  
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="df74b-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="df74b-123">See Also</span></span>  
 [<span data-ttu-id="df74b-124">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="df74b-124">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)
