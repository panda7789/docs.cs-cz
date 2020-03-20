---
title: Výjimky za běhu v nativních aplikací .NET
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 12df2ef7bf6e86a60dfa4c130f35969e72ac5211
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180940"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="a4384-102">Výjimky za běhu v nativních aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="a4384-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="a4384-103">Je důležité otestovat sestavení verze aplikace univerzální platformy Windows na cílových platformách, protože konfigurace ladění a vydání jsou zcela odlišné.</span><span class="sxs-lookup"><span data-stu-id="a4384-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="a4384-104">Ve výchozím nastavení používá konfigurace ladění ke kompilaci aplikace runtime .NET Core, ale konfigurace vydání používá .NET Native ke kompilaci aplikace do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a4384-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a4384-105">Informace o práci s [ChybějícíMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) výjimky, které se mohou vyskytnou při testování vydání verze aplikace, naleznete v části Krok 4: Ručně vyřešit chybějící metadata: v [tématu Začínáme,](getting-started-with-net-native.md) jakož i [Reflexe a .NET nativní](reflection-and-net-native.md) a [runtime směrnice (rd.xml) Konfigurační soubor Odkaz](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="a4384-105">For information on dealing with the [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see "Step 4: Manually resolve missing metadata: in the [Getting Started](getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="a4384-106">Ladění a vydání sestavení</span><span class="sxs-lookup"><span data-stu-id="a4384-106">Debug and release builds</span></span>  
 <span data-ttu-id="a4384-107">Při ladění sestavení provede proti .NET Core runtime, nebyl akompilován do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a4384-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="a4384-108">Díky tomu jsou všechny služby běžně poskytované za běhu k dispozici pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a4384-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="a4384-109">Na druhou stranu se sestavení verze zkompiluje do nativního kódu pro své cílové platformy, odebere většinu závislostí na externích runčasech a knihovnách a silně optimalizuje kód pro maximální výkon.</span><span class="sxs-lookup"><span data-stu-id="a4384-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="a4384-110">Při ladění vydání sestavení, které jsou kompilovány pomocí .NET Native:</span><span class="sxs-lookup"><span data-stu-id="a4384-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
- <span data-ttu-id="a4384-111">Použijete ladicí modul .NET Native, který se liší od běžných ladicích nástrojů .NET.</span><span class="sxs-lookup"><span data-stu-id="a4384-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
- <span data-ttu-id="a4384-112">Velikost spustitelného souboru je co nejvíce snížena.</span><span class="sxs-lookup"><span data-stu-id="a4384-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="a4384-113">Jedním ze způsobů, které .NET Native zmenšuje velikost spustitelného souboru, je výrazné oříznutí zpráv výjimek modulu runtime, což je téma popsané podrobněji v části [Zprávy výjimek modulu Runtime.](#Messages)</span><span class="sxs-lookup"><span data-stu-id="a4384-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
- <span data-ttu-id="a4384-114">Váš kód je silně optimalizován.</span><span class="sxs-lookup"><span data-stu-id="a4384-114">Your code is heavily optimized.</span></span> <span data-ttu-id="a4384-115">To znamená, že vkládání se používá, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="a4384-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="a4384-116">(Vkládání přesune kód z externích rutin do volající rutiny.)   Skutečnost, že .NET Native poskytuje specializované runtime a implementuje agresivní vkládání ovlivňuje zásobník volání, který se zobrazí při ladění.</span><span class="sxs-lookup"><span data-stu-id="a4384-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="a4384-117">Další informace naleznete v části [Zásobník volání runtime.](#CallStack)</span><span class="sxs-lookup"><span data-stu-id="a4384-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4384-118">Můžete určit, zda ladění a vydání sestavení jsou kompilovány s řetězcem nástrojů .NET Nativní kontrolou nebo zrušením zaškrtnutí **compile with .NET Nativní řetězec nástrojů** box.</span><span class="sxs-lookup"><span data-stu-id="a4384-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="a4384-119">Upozorňujeme však, že Windows Store bude vždy zkompilovat produkční verzi vaší aplikace pomocí řetězce nástrojů .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a4384-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>
## <a name="runtime-exception-messages"></a><span data-ttu-id="a4384-120">Zprávy o výjimce za běhu</span><span class="sxs-lookup"><span data-stu-id="a4384-120">Runtime exception messages</span></span>  
 <span data-ttu-id="a4384-121">Chcete-li minimalizovat velikost spustitelného souboru aplikace, nativní rozhraní .NET neobsahuje úplný text zpráv výjimek.</span><span class="sxs-lookup"><span data-stu-id="a4384-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="a4384-122">V důsledku toho runtime výjimky vyvolány v sestavení verze nemusí zobrazit úplný text zprávy výjimky.</span><span class="sxs-lookup"><span data-stu-id="a4384-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="a4384-123">Místo toho text může sestávat z podřetězce spolu s odkazem následovat další informace.</span><span class="sxs-lookup"><span data-stu-id="a4384-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="a4384-124">Informace o výjimce se mohou například zobrazit jako:</span><span class="sxs-lookup"><span data-stu-id="a4384-124">For example, the exception information may appear as:</span></span>  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="a4384-125">Pokud potřebujete úplnou zprávu o výjimce, spusťte místo toho sestavení ladění.</span><span class="sxs-lookup"><span data-stu-id="a4384-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="a4384-126">Například předchozí informace o výjimce z verze sestavení se může zobrazit takto v sestavení ladění:</span><span class="sxs-lookup"><span data-stu-id="a4384-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>
## <a name="runtime-call-stack"></a><span data-ttu-id="a4384-127">Zásobník volání za běhu</span><span class="sxs-lookup"><span data-stu-id="a4384-127">Runtime call stack</span></span>  
 <span data-ttu-id="a4384-128">Z důvodu vkládání a další optimalizace zásobníku volání zobrazené aplikací zkompilované řetězce nástrojů .NET Nativní nemusí pomoci jasně identifikovat cestu k výjimce za běhu.</span><span class="sxs-lookup"><span data-stu-id="a4384-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="a4384-129">Chcete-li získat celý zásobník, spusťte sestavení ladění místo.</span><span class="sxs-lookup"><span data-stu-id="a4384-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4384-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4384-130">See also</span></span>

- [<span data-ttu-id="a4384-131">Ladění nativních univerzálních aplikací systému Windows .NET</span><span class="sxs-lookup"><span data-stu-id="a4384-131">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="a4384-132">Začínáme</span><span class="sxs-lookup"><span data-stu-id="a4384-132">Getting Started</span></span>](getting-started-with-net-native.md)
