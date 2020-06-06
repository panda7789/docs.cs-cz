---
title: Výjimky za běhu v nativních aplikací .NET
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 12df2ef7bf6e86a60dfa4c130f35969e72ac5211
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180940"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="f3eb4-102">Výjimky za běhu v nativních aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="f3eb4-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="f3eb4-103">Je důležité otestovat buildy vydání vaší Univerzální platforma Windows aplikace na svých cílových platformách, protože konfigurace ladění a vydání jsou zcela odlišné.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="f3eb4-104">Ve výchozím nastavení používá konfigurace ladění modul runtime .NET Core ke kompilaci vaší aplikace, ale konfigurace vydané verze používá .NET Native ke kompilaci vaší aplikace do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f3eb4-105">Informace o řešení potíží s výjimkami [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , se kterými se můžete setkat při testování verzí verze vaší aplikace, najdete v tématu "krok 4: Ruční vyřešení chybějících metadat: v tématu [Začínáme](getting-started-with-net-native.md) a také v referenčních souborech pro [reflexi a .NET Native](reflection-and-net-native.md) a [modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="f3eb4-105">For information on dealing with the [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see "Step 4: Manually resolve missing metadata: in the [Getting Started](getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="f3eb4-106">Sestavení ladění a vydaných verzí</span><span class="sxs-lookup"><span data-stu-id="f3eb4-106">Debug and release builds</span></span>  
 <span data-ttu-id="f3eb4-107">Když se sestavení ladění provede proti modulu runtime .NET Core, není zkompilováno do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="f3eb4-108">Díky tomu jsou všechny služby běžně poskytované modulem runtime dostupným pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="f3eb4-109">Na druhé straně sestavení pro vydání se zkompiluje do nativního kódu pro své cílové platformy, odebírá většinu závislostí na externích modulech runtime a knihoven a silně optimalizuje kód pro maximální výkon.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="f3eb4-110">Při ladění sestavení vydaných verzí, která jsou kompilována pomocí .NET Native:</span><span class="sxs-lookup"><span data-stu-id="f3eb4-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
- <span data-ttu-id="f3eb4-111">Použijete modul .NET Native ladění, který se liší od normálních ladicích nástrojů .NET.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
- <span data-ttu-id="f3eb4-112">Velikost spustitelného souboru se zmenší co nejvíce.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="f3eb4-113">Jedním z způsobů, jak .NET Native zmenší velikost spustitelného souboru, je tím, že významně vystřihují zprávy o výjimkách modulu runtime, téma podrobněji popsané v části [zprávy o výjimkách modulu runtime](#Messages) .</span><span class="sxs-lookup"><span data-stu-id="f3eb4-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
- <span data-ttu-id="f3eb4-114">Váš kód je intenzivně optimalizovaný.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-114">Your code is heavily optimized.</span></span> <span data-ttu-id="f3eb4-115">To znamená, že pokud je to možné, používá se vkládání.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="f3eb4-116">(Vkládání kódu přesouvá kód z externích rutin do volající rutiny.)   Fakt, že .NET Native poskytuje specializované prostředí runtime a implementuje agresivní vkládání, má vliv na zásobník volání, který se zobrazí při ladění.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="f3eb4-117">Další informace naleznete v části [zásobník volání modulu runtime](#CallStack) .</span><span class="sxs-lookup"><span data-stu-id="f3eb4-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3eb4-118">Můžete určit, zda jsou sestavení ladění a vydání kompilována pomocí .NET Nativeho řetězu nástroje zaškrtnutím nebo zrušením zaškrtnutí políčka **kompilovat pomocí .NET Nativeho řetězu nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="f3eb4-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="f3eb4-119">Upozorňujeme však, že Windows Store vždy zkompiluje produkční verzi vaší aplikace s řetězcem nástroje .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>
## <a name="runtime-exception-messages"></a><span data-ttu-id="f3eb4-120">Zprávy o výjimkách modulu runtime</span><span class="sxs-lookup"><span data-stu-id="f3eb4-120">Runtime exception messages</span></span>  
 <span data-ttu-id="f3eb4-121">Pro minimalizaci velikosti spustitelného souboru aplikace .NET Native neobsahují úplný text zpráv o výjimkách.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="f3eb4-122">V důsledku toho nemusí běhové výjimky vyvolané v sestavení vydaných verzí zobrazovat úplný text zpráv o výjimkách.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="f3eb4-123">Místo toho se může text skládat z podřetězce spolu s odkazem na Další informace.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="f3eb4-124">Například informace o výjimce mohou vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="f3eb4-124">For example, the exception information may appear as:</span></span>  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="f3eb4-125">Pokud potřebujete zprávu o úplné výjimce, spusťte místo toho sestavení ladění.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="f3eb4-126">Například předchozí informace o výjimce z buildu pro vydání se mohou zobrazit v sestavení ladění následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f3eb4-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>
## <a name="runtime-call-stack"></a><span data-ttu-id="f3eb4-127">Zásobník volání za běhu</span><span class="sxs-lookup"><span data-stu-id="f3eb4-127">Runtime call stack</span></span>  
 <span data-ttu-id="f3eb4-128">Z důvodu vkládání a dalších optimalizací může být zásobník volání zobrazený aplikací zkompilováným řetězcem nástroje .NET Native moci jednoznačně identifikovat cestu k výjimce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="f3eb4-129">Chcete-li získat úplný zásobník, spusťte místo toho sestavení ladění.</span><span class="sxs-lookup"><span data-stu-id="f3eb4-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3eb4-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3eb4-130">See also</span></span>

- [<span data-ttu-id="f3eb4-131">Ladění .NET Native univerzálních aplikací pro Windows</span><span class="sxs-lookup"><span data-stu-id="f3eb4-131">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="f3eb4-132">Začínáme</span><span class="sxs-lookup"><span data-stu-id="f3eb4-132">Getting Started</span></span>](getting-started-with-net-native.md)
