---
title: "Příklad: Řešení potíží s dynamické programování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: de808e333506858d6591dab6c7c06e6a3e9ddabd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="7c415-102">Příklad: Řešení potíží s dynamické programování</span><span class="sxs-lookup"><span data-stu-id="7c415-102">Example: Troubleshooting Dynamic Programming</span></span>
> [!NOTE]
>  <span data-ttu-id="7c415-103">Toto téma se týká .NET nativní Developer Preview, což je předběžná verze softwaru.</span><span class="sxs-lookup"><span data-stu-id="7c415-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="7c415-104">Preview z si můžete stáhnout [webu Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).</span><span class="sxs-lookup"><span data-stu-id="7c415-104">You can download the preview from the [Microsoft Connect website](http://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="7c415-105">Ne všechny selhání vyhledávání metadata v aplikace vyvinuté pomocí [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu způsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="7c415-105">Not all metadata lookup failures in apps developed using the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain result in an exception.</span></span>  <span data-ttu-id="7c415-106">Některé můžete manifest nepředvídatelně v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7c415-106">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="7c415-107">Následující příklad ukazuje narušení přístupu způsobené odkazující na objekt s hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="7c415-107">The following example shows an access violation caused by referencing a null object:</span></span>  
  
```  
Access violation - code c0000005 (first chance)  
App!$3_App::Core::Util::NavigationArgs.Setup  
App!$3_App::Core::Util::NavigationArgs..ctor  
App!$0_App::Gibbon::Util::DesktopNavigationArgs..ctor  
App!$0_App::ViewModels::DesktopAppVM.NavigateToPage  
App!$3_App::Core::ViewModels::AppViewModel.NavigateToFirstPage  
App!$3_App::Core::ViewModels::AppViewModel::<HandleLaunch>d__a.MoveNext  
App!$43_System::Runtime::CompilerServices::AsyncMethodBuilderCore.CallMoveNext  
App!System::Action.InvokeClosedStaticThunk  
App!System::Action.Invoke  
App!$43_System::Threading::Tasks::AwaitTaskContinuation.InvokeAction  
App!$43_System::Threading::SendOrPostCallback.InvokeOpenStaticThunk  
[snip]  
```  
  
 <span data-ttu-id="7c415-108">Nyní si vyzkoušíte odstranění této výjimky pomocí přístup tří kroků uvedených v části "Vyřešit ručně chybí metadata" [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="7c415-108">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="7c415-109">Co dělal aplikace?</span><span class="sxs-lookup"><span data-stu-id="7c415-109">What was the app doing?</span></span>  
 <span data-ttu-id="7c415-110">Nejprve si všimněte si `async` stroje – klíčové slovo ve základní zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7c415-110">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="7c415-111">Určení, co aplikace opravdu dělal `async` metoda může být problematické, protože došlo ke ztrátě kontextu původní volání zásobníku a byla spuštěna `async` kód v jiném podprocesu.</span><span class="sxs-lookup"><span data-stu-id="7c415-111">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="7c415-112">Jsme ale odvodit, že aplikace se pokouší načíst stránku s jeho první.</span><span class="sxs-lookup"><span data-stu-id="7c415-112">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="7c415-113">K implementaci pro `NavigationArgs.Setup`, následující kód způsobila narušení přístupu:</span><span class="sxs-lookup"><span data-stu-id="7c415-113">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 <span data-ttu-id="7c415-114">V tomto případě `LayoutVM` vlastnost na `AppViewModel.Current` byla **null**.</span><span class="sxs-lookup"><span data-stu-id="7c415-114">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="7c415-115">Některé absenci metadata způsobeno rozdíl jemně chování a výsledkem vlastnost probíhá Neinicializovaný místo sady jako aplikace očekává.</span><span class="sxs-lookup"><span data-stu-id="7c415-115">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="7c415-116">Nastavení zarážky v kódu kde `LayoutVM` by inicializované může vyvolat light na situaci.</span><span class="sxs-lookup"><span data-stu-id="7c415-116">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="7c415-117">Všimněte si však, že `LayoutVM`na typ je `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span><span class="sxs-lookup"><span data-stu-id="7c415-117">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="7c415-118">Jedná se o direktivu pouze metadata, pokud v souboru rd.xml:</span><span class="sxs-lookup"><span data-stu-id="7c415-118">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="7c415-119">Pravděpodobně kandidátem na selhání je, že `App.Core.ViewModels.Layout.LayoutApplicationVM` chybí metadata, protože je v jiný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="7c415-119">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="7c415-120">V takovém případě přidání direktivy modulu runtime pro `App.Core.ViewModels` vyřešit problém.</span><span class="sxs-lookup"><span data-stu-id="7c415-120">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="7c415-121">Hlavní příčinou došlo volání rozhraní API <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> metoda, která vrátila **null**, a aplikace bezobslužně ignorovány problém, dokud došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="7c415-121">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="7c415-122">V dynamické programování vhodné při použití rozhraní API reflexe pod [!INCLUDE[net_native](../../../includes/net-native-md.md)] je použití <xref:System.Type.GetType%2A?displayProperty=nameWithType> přetížení, které způsobí výjimku při selhání.</span><span class="sxs-lookup"><span data-stu-id="7c415-122">In dynamic programming, a good practice when using reflection APIs under [!INCLUDE[net_native](../../../includes/net-native-md.md)] is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="7c415-123">Je to izolované případ?</span><span class="sxs-lookup"><span data-stu-id="7c415-123">Is this an isolated case?</span></span>  
 <span data-ttu-id="7c415-124">Další problémy může také nastat při použití `App.Core.ViewModels`.</span><span class="sxs-lookup"><span data-stu-id="7c415-124">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="7c415-125">Musíte se rozhodnout, zda je vhodné identifikace a opravě jednotlivých chybí metadata výjimkách nebo což šetří čas a přidání direktivy pro třídu větší typů.</span><span class="sxs-lookup"><span data-stu-id="7c415-125">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="7c415-126">Zde přidání `dynamic` metadata pro `App.Core.ViewModels` může být nejlepším řešením, pokud výsledný zvýšení velikosti binární výstup není problém.</span><span class="sxs-lookup"><span data-stu-id="7c415-126">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="7c415-127">By mohla být přepsána kód?</span><span class="sxs-lookup"><span data-stu-id="7c415-127">Could the code be rewritten?</span></span>  
 <span data-ttu-id="7c415-128">Použití aplikace `typeof(LayoutApplicationVM)` místo `Type.GetType("LayoutApplicationVM")`, může mít zachovaná řetězu nástroj `browse` metadat.</span><span class="sxs-lookup"><span data-stu-id="7c415-128">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="7c415-129">Ale je stále nebude vytvořili `invoke` metadata, která by vedly k [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimka při vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="7c415-129">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="7c415-130">Pokud chcete zabránit výjimku, stále nutné přidání direktivy modulu runtime pro obor názvů nebo typ, který určuje `dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="7c415-130">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="7c415-131">Informace o direktivy modulu runtime najdete v tématu [direktivy modulu Runtime (rd.xml) referenci na konfigurační soubor](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="7c415-131">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c415-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c415-132">See Also</span></span>  
 [<span data-ttu-id="7c415-133">Začínáme</span><span class="sxs-lookup"><span data-stu-id="7c415-133">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="7c415-134">Příklad: Zpracování výjimek, pokud vazba dat</span><span class="sxs-lookup"><span data-stu-id="7c415-134">Example: Handling Exceptions When Binding Data</span></span>](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
