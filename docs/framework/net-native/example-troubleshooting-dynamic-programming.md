---
title: 'Příklad: řešení potíží s dynamickým programováním'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
ms.openlocfilehash: ff179854066d024a89cb5a84a19d0b9bb054d6e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128444"
---
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="4d389-102">Příklad: řešení potíží s dynamickým programováním</span><span class="sxs-lookup"><span data-stu-id="4d389-102">Example: Troubleshooting Dynamic Programming</span></span>
> [!NOTE]
> <span data-ttu-id="4d389-103">Toto téma se týká .NET Native Developer Preview, což je předběžná verze softwaru.</span><span class="sxs-lookup"><span data-stu-id="4d389-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="4d389-104">Verzi Preview si můžete stáhnout z [webu Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).</span><span class="sxs-lookup"><span data-stu-id="4d389-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="4d389-105">Ne všechna selhání při vyhledávání metadat v aplikacích vyvinutých pomocí řetězu nástrojů .NET Native způsobily výjimku.</span><span class="sxs-lookup"><span data-stu-id="4d389-105">Not all metadata lookup failures in apps developed using the .NET Native tool chain result in an exception.</span></span>  <span data-ttu-id="4d389-106">Některé mohou v aplikaci v nepředvídatelných způsobech manifestovat.</span><span class="sxs-lookup"><span data-stu-id="4d389-106">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="4d389-107">Následující příklad ukazuje narušení přístupu způsobené odkazem na objekt s hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="4d389-107">The following example shows an access violation caused by referencing a null object:</span></span>  
  
```output
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
  
 <span data-ttu-id="4d389-108">Pojďme se pokusit tuto výjimku vyřešit pomocí třech kroků popsaných v části "Ruční řešení chybějících metadat" v [Začínáme](getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="4d389-108">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="4d389-109">Jakou aplikaci dělá?</span><span class="sxs-lookup"><span data-stu-id="4d389-109">What was the app doing?</span></span>  
 <span data-ttu-id="4d389-110">První věc, kterou je potřeba poznamenat, je mechanismus `async`ho klíčového slova na bázi zásobníku.</span><span class="sxs-lookup"><span data-stu-id="4d389-110">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="4d389-111">Určení toho, co aplikace skutečně prováděla v `async` metoda může být problematické, protože zásobník ztratil kontext původního volání a spustil kód `async` v jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="4d389-111">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="4d389-112">Můžeme ale odvodit, že se aplikace pokouší načíst první stránku.</span><span class="sxs-lookup"><span data-stu-id="4d389-112">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="4d389-113">V implementaci pro `NavigationArgs.Setup`následující kód způsobil porušení přístupu:</span><span class="sxs-lookup"><span data-stu-id="4d389-113">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 <span data-ttu-id="4d389-114">V tomto případě vlastnost `LayoutVM` v `AppViewModel.Current` měla **hodnotu null**.</span><span class="sxs-lookup"><span data-stu-id="4d389-114">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="4d389-115">Některé z absencí metadat způsobily malý rozdíl v chování a způsobily neinicializované vlastnosti namísto set, jak očekává aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d389-115">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="4d389-116">Nastavení zarážky v kódu, kde `LayoutVM` měla být inicializována, mohou vyvolat světlo v situaci.</span><span class="sxs-lookup"><span data-stu-id="4d389-116">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="4d389-117">Upozorňujeme však, že typ `LayoutVM`je `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span><span class="sxs-lookup"><span data-stu-id="4d389-117">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="4d389-118">V souboru Rd. XML je zatím přítomna jediná direktiva metadat:</span><span class="sxs-lookup"><span data-stu-id="4d389-118">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="4d389-119">Pravděpodobným kandidátem na selhání je, že `App.Core.ViewModels.Layout.LayoutApplicationVM` chybí metadata, protože se nachází v jiném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4d389-119">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="4d389-120">V tomto případě přidání direktivy modulu runtime pro `App.Core.ViewModels` vyřešili problém.</span><span class="sxs-lookup"><span data-stu-id="4d389-120">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="4d389-121">Hlavní příčinou bylo volání rozhraní API k metodě <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType>, která vrátila **hodnotu null**, a aplikace tiše tuto chybu ignorovala, dokud nedošlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="4d389-121">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="4d389-122">V dynamickém programování je vhodný postup při použití rozhraní API pro reflexi v rámci .NET Native použít přetížení <xref:System.Type.GetType%2A?displayProperty=nameWithType>, které vyvolávají výjimku při selhání.</span><span class="sxs-lookup"><span data-stu-id="4d389-122">In dynamic programming, a good practice when using reflection APIs under .NET Native is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="4d389-123">Jedná se o izolovaný případ?</span><span class="sxs-lookup"><span data-stu-id="4d389-123">Is this an isolated case?</span></span>  
 <span data-ttu-id="4d389-124">K dalším potížím může dojít také při použití `App.Core.ViewModels`.</span><span class="sxs-lookup"><span data-stu-id="4d389-124">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="4d389-125">Je nutné rozhodnout, zda má být identifikována a opravena chybějící výjimka metadat, nebo ušetřit čas a přidat direktivy pro větší třídu typů.</span><span class="sxs-lookup"><span data-stu-id="4d389-125">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="4d389-126">Tady je přidání metadat `dynamic` pro `App.Core.ViewModels` může být nejlepší přístup, pokud výsledná velikost výstupního binárního souboru není problémem.</span><span class="sxs-lookup"><span data-stu-id="4d389-126">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="4d389-127">Byl kód přepsán?</span><span class="sxs-lookup"><span data-stu-id="4d389-127">Could the code be rewritten?</span></span>  
 <span data-ttu-id="4d389-128">Pokud aplikace použila `typeof(LayoutApplicationVM)` místo `Type.GetType("LayoutApplicationVM")`, řetěz nástrojů by mohl uchovávat `browse` metadata.</span><span class="sxs-lookup"><span data-stu-id="4d389-128">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="4d389-129">Přesto ale nevytvořila metadata `invoke`, což by vedlo k výjimce [MissingMetadataException](missingmetadataexception-class-net-native.md) při vytváření instance typu.</span><span class="sxs-lookup"><span data-stu-id="4d389-129">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="4d389-130">Chcete-li zabránit výjimce, je stále nutné přidat direktivu modulu runtime pro obor názvů nebo typ, který určuje zásadu `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="4d389-130">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="4d389-131">Informace o direktivách modulu runtime naleznete v tématu [reference ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="4d389-131">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d389-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d389-132">See also</span></span>

- [<span data-ttu-id="4d389-133">Začínáme</span><span class="sxs-lookup"><span data-stu-id="4d389-133">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="4d389-134">Příklad: Zpracování výjimek při vázání dat</span><span class="sxs-lookup"><span data-stu-id="4d389-134">Example: Handling Exceptions When Binding Data</span></span>](example-handling-exceptions-when-binding-data.md)
