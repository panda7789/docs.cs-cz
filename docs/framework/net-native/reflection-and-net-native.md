---
title: Reflexe a .NET Native
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e248071a0d35c5552976e5e4663094b76ee162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="reflection-and-net-native"></a><span data-ttu-id="45894-102">Reflexe a .NET Native</span><span class="sxs-lookup"><span data-stu-id="45894-102">Reflection and .NET Native</span></span>
<span data-ttu-id="45894-103">Ke správě podporuje vývoj metaprogramování prostřednictvím rozhraní API reflexe v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45894-103">In the .NET Framework, managed development supports metaprogramming through the reflection API.</span></span> <span data-ttu-id="45894-104">Reflexe umožňuje zkontrolovat objekty v aplikaci, volat metody pro objekty zjištěné prostřednictvím kontroly, generování nových typů v době běhu a podporuje mnoho dalších scénářů dynamický kód.</span><span class="sxs-lookup"><span data-stu-id="45894-104">Reflection allows you to inspect objects in an app, call methods on objects discovered through inspection, generate new types at run time, and supports many other dynamic code scenarios.</span></span> <span data-ttu-id="45894-105">Podporuje také serializace a deserializace, což umožňuje objektu hodnoty polí jako trvalý, a později obnovit.</span><span class="sxs-lookup"><span data-stu-id="45894-105">It also supports serialization and deserialization, which allows an object's field values to be persisted and later restored.</span></span> <span data-ttu-id="45894-106">Všechny tyto scénáře vyžadují rozhraní .NET Framework za běhu (JIT) kompilátor ke generování nativního kódu na základě metadat k dispozici.</span><span class="sxs-lookup"><span data-stu-id="45894-106">These scenarios all require the .NET Framework just-in-time (JIT) compiler to generate native code based on available metadata.</span></span>  
  
 <span data-ttu-id="45894-107">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Runtime neobsahuje kompilátoru za běhu.</span><span class="sxs-lookup"><span data-stu-id="45894-107">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime doesn't include a JIT compiler.</span></span> <span data-ttu-id="45894-108">Všechny nezbytné nativního kódu v důsledku toho musí vygenerovat předem.</span><span class="sxs-lookup"><span data-stu-id="45894-108">As a result, all necessary native code must be generated in advance.</span></span> <span data-ttu-id="45894-109">Sadu heuristiky slouží k určení, jaký kód by měl být vygenerován, ale tyto heuristiky nelze zahrnují všechny možné metaprogramování scénáře.</span><span class="sxs-lookup"><span data-stu-id="45894-109">A set of heuristics is used to determine what code should be generated, but these heuristics cannot cover all possible metaprogramming scenarios.</span></span>  <span data-ttu-id="45894-110">Proto je nutné zadat pomocné parametry pro tyto scénáře metaprogramování s použitím [direktivy modulu runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="45894-110">Therefore, you must provide hints for these metaprogramming scenarios by using [runtime directives](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="45894-111">Pokud není k dispozici v době běhu nezbytné metadata nebo implementace kód, vyvolá vaší aplikace [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md), nebo [ MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) výjimka.</span><span class="sxs-lookup"><span data-stu-id="45894-111">If the necessary metadata or implementation code is not available at runtime, your app throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md), or [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) exception.</span></span> <span data-ttu-id="45894-112">Jsou k dispozici dva Poradce při potížích, vygeneruje na příslušnou položku pro váš soubor direktivy modulu runtime, který eliminuje výjimka:</span><span class="sxs-lookup"><span data-stu-id="45894-112">Two troubleshooters are available that will generate the appropriate entry for your runtime directives file that eliminates the exception:</span></span>  
  
-   <span data-ttu-id="45894-113">[MissingMetadataException Poradce při potížích s](http://dotnet.github.io/native/troubleshooter/type.html) pro typy.</span><span class="sxs-lookup"><span data-stu-id="45894-113">The [MissingMetadataException troubleshooter](http://dotnet.github.io/native/troubleshooter/type.html) for types.</span></span>  
  
-   <span data-ttu-id="45894-114">[MissingMetadataException Poradce při potížích s](http://dotnet.github.io/native/troubleshooter/method.html) pro metody.</span><span class="sxs-lookup"><span data-stu-id="45894-114">The [MissingMetadataException troubleshooter](http://dotnet.github.io/native/troubleshooter/method.html) for methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45894-115">Přehled procesu .NET Native kompilace, která poskytuje pozadí na důvod, proč je potřeba soubor direktivy modulu runtime, najdete v části [.NET Native a kompilace](../../../docs/framework/net-native/net-native-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="45894-115">For an overview of the .NET Native compilation process that provides background on why a runtime directives file is needed, see [.NET Native and Compilation](../../../docs/framework/net-native/net-native-and-compilation.md).</span></span>  
  
 <span data-ttu-id="45894-116">Kromě toho [!INCLUDE[net_native](../../../includes/net-native-md.md)] neumožňuje, aby odrážela přes soukromé členy knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45894-116">In addition, [!INCLUDE[net_native](../../../includes/net-native-md.md)] doesn't allow you to reflect over private members of the .NET Framework class library.</span></span> <span data-ttu-id="45894-117">Například volání <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> vlastnost k načtení pole rozhraní .NET Framework – třída knihovny typu vrátí pouze veřejné nebo chráněného polí.</span><span class="sxs-lookup"><span data-stu-id="45894-117">For example, a call to the <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> property to retrieve the fields of a .NET Framework class library type returns only public or protected fields.</span></span>  
  
 <span data-ttu-id="45894-118">Následující témata poskytují koncepční a referenční dokumentace, která budete potřebovat k podpoře reflexe a serializace ve svých aplikacích:</span><span class="sxs-lookup"><span data-stu-id="45894-118">The following topics provide the conceptual and reference documentation that you need to support reflection and serialization in your apps:</span></span>  
  
-   [<span data-ttu-id="45894-119">Rozhraní API, která závisí na reflexi</span><span class="sxs-lookup"><span data-stu-id="45894-119">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
-   [<span data-ttu-id="45894-120">Informace o rozhraní API reflexe</span><span class="sxs-lookup"><span data-stu-id="45894-120">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
-   [<span data-ttu-id="45894-121">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="45894-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="45894-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="45894-122">See Also</span></span>  
 [<span data-ttu-id="45894-123">Kompilování aplikací pomocí .NET Native</span><span class="sxs-lookup"><span data-stu-id="45894-123">Compiling Apps with .NET Native</span></span>](../../../docs/framework/net-native/index.md)  
 [<span data-ttu-id="45894-124">.NET Native a kompilace</span><span class="sxs-lookup"><span data-stu-id="45894-124">.NET Native and Compilation</span></span>](../../../docs/framework/net-native/net-native-and-compilation.md)
