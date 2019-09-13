---
title: Výjimky za běhu v nativních aplikací .NET
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68fe50d24ce547e1cad092e3d871c2d0990fd5af
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894978"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="02aaf-102">Výjimky za běhu v nativních aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="02aaf-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="02aaf-103">Je důležité otestovat buildy vydání vaší Univerzální platforma Windows aplikace na svých cílových platformách, protože konfigurace ladění a vydání jsou zcela odlišné.</span><span class="sxs-lookup"><span data-stu-id="02aaf-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="02aaf-104">Ve výchozím nastavení používá konfigurace ladění modul runtime .NET Core ke kompilaci vaší aplikace, ale konfigurace vydané verze používá .NET Native ke kompilaci vaší aplikace do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="02aaf-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="02aaf-105">Informace o tom, jak řešit výjimky [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) , se kterými se můžete setkat při testování verzí verze vaší aplikace, najdete v části Krok 4: Ruční řešení chybějících metadat: v tématu [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md) a také v odkazech na konfigurační soubor direktivy [reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) a [runtime (RD. XML)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="02aaf-105">For information on dealing with the [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see  "Step 4: Manually resolve missing metadata: in the [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="02aaf-106">Sestavení ladění a vydaných verzí</span><span class="sxs-lookup"><span data-stu-id="02aaf-106">Debug and release builds</span></span>  
 <span data-ttu-id="02aaf-107">Když se sestavení ladění provede proti modulu runtime .NET Core, není zkompilováno do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="02aaf-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="02aaf-108">Díky tomu jsou všechny služby běžně poskytované modulem runtime dostupným pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="02aaf-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="02aaf-109">Na druhé straně sestavení pro vydání se zkompiluje do nativního kódu pro své cílové platformy, odebírá většinu závislostí na externích modulech runtime a knihoven a silně optimalizuje kód pro maximální výkon.</span><span class="sxs-lookup"><span data-stu-id="02aaf-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="02aaf-110">Při ladění sestavení vydaných verzí, která jsou kompilována pomocí .NET Native:</span><span class="sxs-lookup"><span data-stu-id="02aaf-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
- <span data-ttu-id="02aaf-111">Použijete modul .NET Native ladění, který se liší od normálních ladicích nástrojů .NET.</span><span class="sxs-lookup"><span data-stu-id="02aaf-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
- <span data-ttu-id="02aaf-112">Velikost spustitelného souboru se zmenší co nejvíce.</span><span class="sxs-lookup"><span data-stu-id="02aaf-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="02aaf-113">Jedním z způsobů, jak .NET Native zmenší velikost spustitelného souboru, je tím, že významně vystřihují zprávy o výjimkách modulu runtime, téma podrobněji popsané v části [zprávy o výjimkách modulu runtime](#Messages) .</span><span class="sxs-lookup"><span data-stu-id="02aaf-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
- <span data-ttu-id="02aaf-114">Váš kód je intenzivně optimalizovaný.</span><span class="sxs-lookup"><span data-stu-id="02aaf-114">Your code is heavily optimized.</span></span> <span data-ttu-id="02aaf-115">To znamená, že pokud je to možné, používá se vkládání.</span><span class="sxs-lookup"><span data-stu-id="02aaf-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="02aaf-116">(Vkládání kódu přesouvá kód z externích rutin do volající rutiny.)   Fakt, že .NET Native poskytuje specializované prostředí runtime a implementuje agresivní vkládání, má vliv na zásobník volání, který se zobrazí při ladění.</span><span class="sxs-lookup"><span data-stu-id="02aaf-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="02aaf-117">Další informace naleznete v části [zásobník volání modulu runtime](#CallStack) .</span><span class="sxs-lookup"><span data-stu-id="02aaf-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02aaf-118">Můžete určit, zda jsou sestavení ladění a vydání kompilována pomocí .NET Nativeho řetězu nástroje zaškrtnutím nebo zrušením zaškrtnutí políčka **kompilovat pomocí .NET Nativeho řetězu nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="02aaf-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="02aaf-119">Upozorňujeme však, že Windows Store vždy zkompiluje produkční verzi vaší aplikace s řetězcem nástroje .NET Native.</span><span class="sxs-lookup"><span data-stu-id="02aaf-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a><span data-ttu-id="02aaf-120">Zprávy o výjimkách modulu runtime</span><span class="sxs-lookup"><span data-stu-id="02aaf-120">Runtime exception messages</span></span>  
 <span data-ttu-id="02aaf-121">Pro minimalizaci velikosti spustitelného souboru aplikace .NET Native neobsahují úplný text zpráv o výjimkách.</span><span class="sxs-lookup"><span data-stu-id="02aaf-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="02aaf-122">V důsledku toho nemusí běhové výjimky vyvolané v sestavení vydaných verzí zobrazovat úplný text zpráv o výjimkách.</span><span class="sxs-lookup"><span data-stu-id="02aaf-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="02aaf-123">Místo toho se může text skládat z podřetězce spolu s odkazem na Další informace.</span><span class="sxs-lookup"><span data-stu-id="02aaf-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="02aaf-124">Například informace o výjimce mohou vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="02aaf-124">For example, the exception information may appear as:</span></span>  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="02aaf-125">Pokud potřebujete zprávu o úplné výjimce, spusťte místo toho sestavení ladění.</span><span class="sxs-lookup"><span data-stu-id="02aaf-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="02aaf-126">Například předchozí informace o výjimce z buildu pro vydání se mohou zobrazit v sestavení ladění následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="02aaf-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a><span data-ttu-id="02aaf-127">Zásobník volání za běhu</span><span class="sxs-lookup"><span data-stu-id="02aaf-127">Runtime call stack</span></span>  
 <span data-ttu-id="02aaf-128">Z důvodu vkládání a dalších optimalizací může být zásobník volání zobrazený aplikací zkompilováným řetězcem nástroje .NET Native moci jednoznačně identifikovat cestu k výjimce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="02aaf-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="02aaf-129">Chcete-li získat úplný zásobník, spusťte místo toho sestavení ladění.</span><span class="sxs-lookup"><span data-stu-id="02aaf-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02aaf-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02aaf-130">See also</span></span>

- [<span data-ttu-id="02aaf-131">Ladění .NET Native univerzálních aplikací pro Windows</span><span class="sxs-lookup"><span data-stu-id="02aaf-131">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="02aaf-132">Začínáme</span><span class="sxs-lookup"><span data-stu-id="02aaf-132">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
