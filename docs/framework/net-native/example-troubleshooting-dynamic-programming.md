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
ms.workload: dotnet
ms.openlocfilehash: fdf3f12b325282b048420f57befa752f3f3f6803
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="example-troubleshooting-dynamic-programming"></a>Příklad: Řešení potíží s dynamické programování
> [!NOTE]
>  Toto téma se týká .NET nativní Developer Preview, což je předběžná verze softwaru. Preview z si můžete stáhnout [webu Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).  
  
 Ne všechny selhání vyhledávání metadata v aplikace vyvinuté pomocí [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu způsobí výjimku.  Některé můžete manifest nepředvídatelně v aplikaci.  Následující příklad ukazuje narušení přístupu způsobené odkazující na objekt s hodnotou null:  
  
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
  
 Nyní si vyzkoušíte odstranění této výjimky pomocí přístup tří kroků uvedených v části "Vyřešit ručně chybí metadata" [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md).  
  
## <a name="what-was-the-app-doing"></a>Co dělal aplikace?  
 Nejprve si všimněte si `async` stroje – klíčové slovo ve základní zásobníku.  Určení, co aplikace opravdu dělal `async` metoda může být problematické, protože došlo ke ztrátě kontextu původní volání zásobníku a byla spuštěna `async` kód v jiném podprocesu. Jsme ale odvodit, že aplikace se pokouší načíst stránku s jeho první.  K implementaci pro `NavigationArgs.Setup`, následující kód způsobila narušení přístupu:  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 V tomto případě `LayoutVM` vlastnost na `AppViewModel.Current` byla **null**.  Některé absenci metadata způsobeno rozdíl jemně chování a výsledkem vlastnost probíhá Neinicializovaný místo sady jako aplikace očekává.  Nastavení zarážky v kódu kde `LayoutVM` by inicializované může vyvolat light na situaci.  Všimněte si však, že `LayoutVM`na typ je `App.Core.ViewModels.Layout.LayoutApplicationVM`.  Jedná se o direktivu pouze metadata, pokud v souboru rd.xml:  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 Pravděpodobně kandidátem na selhání je, že `App.Core.ViewModels.Layout.LayoutApplicationVM` chybí metadata, protože je v jiný obor názvů.  
  
 V takovém případě přidání direktivy modulu runtime pro `App.Core.ViewModels` vyřešit problém. Hlavní příčinou došlo volání rozhraní API <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> metoda, která vrátila **null**, a aplikace bezobslužně ignorovány problém, dokud došlo k chybě.  
  
 V dynamické programování vhodné při použití rozhraní API reflexe pod [!INCLUDE[net_native](../../../includes/net-native-md.md)] je použití <xref:System.Type.GetType%2A?displayProperty=nameWithType> přetížení, které způsobí výjimku při selhání.  
  
## <a name="is-this-an-isolated-case"></a>Je to izolované případ?  
 Další problémy může také nastat při použití `App.Core.ViewModels`.  Musíte se rozhodnout, zda je vhodné identifikace a opravě jednotlivých chybí metadata výjimkách nebo což šetří čas a přidání direktivy pro třídu větší typů.  Zde přidání `dynamic` metadata pro `App.Core.ViewModels` může být nejlepším řešením, pokud výsledný zvýšení velikosti binární výstup není problém.  
  
## <a name="could-the-code-be-rewritten"></a>By mohla být přepsána kód?  
 Použití aplikace `typeof(LayoutApplicationVM)` místo `Type.GetType("LayoutApplicationVM")`, může mít zachovaná řetězu nástroj `browse` metadat.  Ale je stále nebude vytvořili `invoke` metadata, která by vedly k [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimka při vytvoření instance typu. Pokud chcete zabránit výjimku, stále nutné přidání direktivy modulu runtime pro obor názvů nebo typ, který určuje `dynamic` zásad. Informace o direktivy modulu runtime najdete v tématu [direktivy modulu Runtime (rd.xml) referenci na konfigurační soubor](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Příklad: Zpracování výjimek při vázání dat](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
