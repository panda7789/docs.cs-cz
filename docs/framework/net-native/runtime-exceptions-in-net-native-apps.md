---
title: Výjimky za běhu v nativních aplikací .NET
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06e07c41d398c0792094b4481a38c69b2ba73004
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208277"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="81e70-102">Výjimky za běhu v nativních aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="81e70-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="81e70-103">Je důležité, otestovat buildy vydaných verzí vaší aplikace pro univerzální platformu Windows na jejich cílové platformy, protože jsou zcela odlišná konfigurace debug a release.</span><span class="sxs-lookup"><span data-stu-id="81e70-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="81e70-104">Ve výchozím nastavení konfiguraci ladění používá modul runtime .NET Core pro kompilaci aplikace ale konfiguraci vydané verze používá .NET Native pro kompilaci aplikace do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="81e70-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81e70-105">Informace pro řešení inovací [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky, které vám dává možnost Při testování verze vaší aplikace najdete v tématu "krok 4: Ruční vyřešení chybějí metadata: v [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md) téma, stejně jako [reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) a [direktivy modulu Runtime (rd.xml) odkaz na soubor konfigurace](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="81e70-105">For information on dealing with the [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see  "Step 4: Manually resolve missing metadata: in the [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="81e70-106">Ladění a sestavení pro vydání</span><span class="sxs-lookup"><span data-stu-id="81e70-106">Debug and release builds</span></span>  
 <span data-ttu-id="81e70-107">Když sestavení pro ladění spuštěn proti modulu runtime .NET Core, nebyl byl zkompilován do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="81e70-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="81e70-108">Díky tomu všechny služby obvykle poskytuje modul runtime, které jsou k dispozici pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="81e70-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="81e70-109">Na druhé straně sestavení pro vydání kompiluje do nativního kódu pro jeho cílové platformy, odebere většina závislostí na externí moduly runtime a knihovny a silně optimalizuje kód pro maximální výkon.</span><span class="sxs-lookup"><span data-stu-id="81e70-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="81e70-110">Při ladění buildů vydaných verzí, které jsou kompilovány pomocí .NET Native:</span><span class="sxs-lookup"><span data-stu-id="81e70-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
-   <span data-ttu-id="81e70-111">Používáte .NET Native ladicího stroje, který se liší od normální .NET nástroje pro ladění.</span><span class="sxs-lookup"><span data-stu-id="81e70-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
-   <span data-ttu-id="81e70-112">Spustitelný soubor je zmenšení co největší míře.</span><span class="sxs-lookup"><span data-stu-id="81e70-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="81e70-113">Jedním ze způsobů, .NET Native snižuje velikost spustitelný soubor je výrazně ořezávání zprávy výjimek modulu runtime, větší podrobně popsány v tématu [zprávy výjimek modulu Runtime](#Messages) oddílu.</span><span class="sxs-lookup"><span data-stu-id="81e70-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
-   <span data-ttu-id="81e70-114">Váš kód je silně optimalizovaná.</span><span class="sxs-lookup"><span data-stu-id="81e70-114">Your code is heavily optimized.</span></span> <span data-ttu-id="81e70-115">To znamená, že vkládání se používá, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="81e70-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="81e70-116">(Vkládání přesune kódu z externího rutin do volání rutiny.)   Skutečnost, že .NET Native poskytuje specializované modulu runtime a implementuje agresivní vkládání ovlivňuje zásobníku volání, který se zobrazí při ladění.</span><span class="sxs-lookup"><span data-stu-id="81e70-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="81e70-117">Další informace najdete v tématu [zásobníku volání modulu Runtime](#CallStack) oddílu.</span><span class="sxs-lookup"><span data-stu-id="81e70-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81e70-118">Můžete řídit, zda sestavení ladění a vydání se kompilují pomocí .NET Native řetězce nástrojů zaškrtnutím nebo zrušením zaškrtnutí **kompilovat s .NET Native řetězce nástrojů** pole.</span><span class="sxs-lookup"><span data-stu-id="81e70-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="81e70-119">Všimněte si však, že Windows Store vždy kompilovat produkční verzi vaší aplikace pomocí .NET Native řetězec nástroje.</span><span class="sxs-lookup"><span data-stu-id="81e70-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a><span data-ttu-id="81e70-120">Zprávy výjimek modulu runtime</span><span class="sxs-lookup"><span data-stu-id="81e70-120">Runtime exception messages</span></span>  
 <span data-ttu-id="81e70-121">Chcete-li minimalizovat velikost spustitelný soubor aplikace .NET Native neobsahuje celý text zprávy o výjimkách.</span><span class="sxs-lookup"><span data-stu-id="81e70-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="81e70-122">Modul runtime výjimky vyvolané v sestaveních pro vydání v důsledku toho nemusí zobrazit celý text zprávy o výjimkách.</span><span class="sxs-lookup"><span data-stu-id="81e70-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="81e70-123">Místo toho může obsahovat text podřetězec spolu s odkazem pro další informace.</span><span class="sxs-lookup"><span data-stu-id="81e70-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="81e70-124">Informace o výjimce může například zobrazit jako:</span><span class="sxs-lookup"><span data-stu-id="81e70-124">For example, the exception information may appear as:</span></span>  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="81e70-125">Pokud je třeba zpráva o výjimce dokončeno, spusťte sestavení pro ladění.</span><span class="sxs-lookup"><span data-stu-id="81e70-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="81e70-126">Předchozí informace o výjimce ze sestavení pro vydání může například vypadat takto v laděném sestavení:</span><span class="sxs-lookup"><span data-stu-id="81e70-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a><span data-ttu-id="81e70-127">Zásobník volání modulu runtime</span><span class="sxs-lookup"><span data-stu-id="81e70-127">Runtime call stack</span></span>  
 <span data-ttu-id="81e70-128">Z důvodu vkládání a další optimalizace zásobník volání zobrazí aplikací zkompilován s .NET Native řetězce nástrojů nemusí vám pomohou cestu k výjimku při běhu se tak jasně identifikovat.</span><span class="sxs-lookup"><span data-stu-id="81e70-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="81e70-129">Pokud chcete získat úplný zásobník, spusťte místo toho sestavení pro ladění.</span><span class="sxs-lookup"><span data-stu-id="81e70-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e70-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81e70-130">See also</span></span>

- [<span data-ttu-id="81e70-131">Ladění univerzálních aplikací pro .NET Native Windows</span><span class="sxs-lookup"><span data-stu-id="81e70-131">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="81e70-132">Začínáme</span><span class="sxs-lookup"><span data-stu-id="81e70-132">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
