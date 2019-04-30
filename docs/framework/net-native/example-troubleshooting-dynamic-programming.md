---
title: 'Příklad: Řešení potíží s dynamickým programováním'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af71c4916a2abdeb019e538a33ad05efa727e720
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868781"
---
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="d0bf4-102">Příklad: Řešení potíží s dynamickým programováním</span><span class="sxs-lookup"><span data-stu-id="d0bf4-102">Example: Troubleshooting Dynamic Programming</span></span>
> [!NOTE]
>  <span data-ttu-id="d0bf4-103">Toto téma odkazuje na .NET Native Developer Preview, což je předběžná verze softwaru.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="d0bf4-104">Preview z si můžete stáhnout [webu Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).</span><span class="sxs-lookup"><span data-stu-id="d0bf4-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="d0bf4-105">Ne všechny metadat selhání vyhledávání v aplikacích vyvinutých pomocí [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu vést k výjimce.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-105">Not all metadata lookup failures in apps developed using the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain result in an exception.</span></span>  <span data-ttu-id="d0bf4-106">Některé můžou výsledkem může být nepředvídatelnými způsoby, jak v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-106">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="d0bf4-107">Následující příklad ukazuje narušení přístupu způsobené odkazující na objekt s hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="d0bf4-107">The following example shows an access violation caused by referencing a null object:</span></span>  
  
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
  
 <span data-ttu-id="d0bf4-108">Nyní si vyzkoušíte odstranění této výjimky pomocí přístupu tří kroků uvedených v části "Ručně vyřešit chybějí metadata" [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="d0bf4-108">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="d0bf4-109">Co dělal aplikace?</span><span class="sxs-lookup"><span data-stu-id="d0bf4-109">What was the app doing?</span></span>  
 <span data-ttu-id="d0bf4-110">První věc, kterou si je `async` stroje – klíčové slovo základní zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-110">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="d0bf4-111">Určení, co aplikace skutečně dělal `async` metoda může být problematické, protože došlo ke ztrátě kontextu původní volání zásobníku a bylo spuštěno `async` kód v jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-111">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="d0bf4-112">Ale můžeme odvodit, že aplikace se pokouší načíst jeho první stránky.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-112">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="d0bf4-113">V implementaci pro `NavigationArgs.Setup`, následující kód způsobil narušení přístupu:</span><span class="sxs-lookup"><span data-stu-id="d0bf4-113">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 <span data-ttu-id="d0bf4-114">V takovém případě `LayoutVM` vlastnost `AppViewModel.Current` byl **null**.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-114">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="d0bf4-115">Některé neexistence metadata způsobit drobné chování rozdíl a výsledkem vlastnost se neinicializované místo sady, jako aplikace očekává.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-115">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="d0bf4-116">Nastavením zarážky v kódu kde `LayoutVM` by byl inicializován může vyvolat světla na situaci.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-116">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="d0bf4-117">Mějte však na paměti, která `LayoutVM`jeho typ je `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-117">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="d0bf4-118">Zatím součástí soubor rd.xml pouze metadata direktiva je:</span><span class="sxs-lookup"><span data-stu-id="d0bf4-118">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="d0bf4-119">Kandidát pravděpodobnost selhání je, že `App.Core.ViewModels.Layout.LayoutApplicationVM` chybí metadata, protože se jiný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-119">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="d0bf4-120">V takovém případě přidání direktivy modulu runtime pro `App.Core.ViewModels` vyřešení problému.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-120">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="d0bf4-121">Původní příčina volání rozhraní API k <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> metodu, která vrátila **null**, a aplikace tiše ignorováno problém, dokud došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-121">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="d0bf4-122">V dynamické programování, je vhodné při použití reflexe rozhraní API v rámci [!INCLUDE[net_native](../../../includes/net-native-md.md)] , je použít <xref:System.Type.GetType%2A?displayProperty=nameWithType> přetížení, které vyvolají výjimku při selhání.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-122">In dynamic programming, a good practice when using reflection APIs under [!INCLUDE[net_native](../../../includes/net-native-md.md)] is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="d0bf4-123">Je to izolované případu?</span><span class="sxs-lookup"><span data-stu-id="d0bf4-123">Is this an isolated case?</span></span>  
 <span data-ttu-id="d0bf4-124">Další problémy mohou nastat také při použití `App.Core.ViewModels`.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-124">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="d0bf4-125">Musíte se rozhodnout, zda je vhodné identifikace a opravuje chybějící výjimka metadat nebo šetří čas a přidání direktivy pro větší třídy typů.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-125">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="d0bf4-126">Tady, přidání `dynamic` metadata pro `App.Core.ViewModels` může být nejlepším řešením, pokud výsledný nárůst velikosti výstupního binárního souboru není problém.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-126">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="d0bf4-127">Může být přepsán kód?</span><span class="sxs-lookup"><span data-stu-id="d0bf4-127">Could the code be rewritten?</span></span>  
 <span data-ttu-id="d0bf4-128">Pokud aplikace použili `typeof(LayoutApplicationVM)` místo `Type.GetType("LayoutApplicationVM")`, může mít zachovány řetězce nástrojů `browse` metadat.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-128">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="d0bf4-129">Ale je stále by vytvořili `invoke` metadat, které by vedly k [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) při vytváření instance typu došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-129">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="d0bf4-130">Aby se zabránilo výjimky, by stále musíte přidat direktivy modulu runtime pro obor názvů nebo typ, který určuje `dynamic` zásad.</span><span class="sxs-lookup"><span data-stu-id="d0bf4-130">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="d0bf4-131">Informace o direktivy modulu runtime, najdete v článku [direktivy modulu Runtime (rd.xml) odkaz na soubor konfigurace](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="d0bf4-131">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0bf4-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0bf4-132">See also</span></span>

- [<span data-ttu-id="d0bf4-133">Začínáme</span><span class="sxs-lookup"><span data-stu-id="d0bf4-133">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="d0bf4-134">Příklad: Zpracování výjimek při vázání dat</span><span class="sxs-lookup"><span data-stu-id="d0bf4-134">Example: Handling Exceptions When Binding Data</span></span>](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
