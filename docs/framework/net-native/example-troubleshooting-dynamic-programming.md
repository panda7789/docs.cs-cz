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
# <a name="example-troubleshooting-dynamic-programming"></a>Příklad: Řešení potíží s dynamickým programováním
> [!NOTE]
>  Toto téma odkazuje na .NET Native Developer Preview, což je předběžná verze softwaru. Preview z si můžete stáhnout [webu Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).  
  
 Ne všechny metadat selhání vyhledávání v aplikacích vyvinutých pomocí [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu vést k výjimce.  Některé můžou výsledkem může být nepředvídatelnými způsoby, jak v aplikaci.  Následující příklad ukazuje narušení přístupu způsobené odkazující na objekt s hodnotou null:  
  
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
  
 Nyní si vyzkoušíte odstranění této výjimky pomocí přístupu tří kroků uvedených v části "Ručně vyřešit chybějí metadata" [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md).  
  
## <a name="what-was-the-app-doing"></a>Co dělal aplikace?  
 První věc, kterou si je `async` stroje – klíčové slovo základní zásobníku.  Určení, co aplikace skutečně dělal `async` metoda může být problematické, protože došlo ke ztrátě kontextu původní volání zásobníku a bylo spuštěno `async` kód v jiném vlákně. Ale můžeme odvodit, že aplikace se pokouší načíst jeho první stránky.  V implementaci pro `NavigationArgs.Setup`, následující kód způsobil narušení přístupu:  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 V takovém případě `LayoutVM` vlastnost `AppViewModel.Current` byl **null**.  Některé neexistence metadata způsobit drobné chování rozdíl a výsledkem vlastnost se neinicializované místo sady, jako aplikace očekává.  Nastavením zarážky v kódu kde `LayoutVM` by byl inicializován může vyvolat světla na situaci.  Mějte však na paměti, která `LayoutVM`jeho typ je `App.Core.ViewModels.Layout.LayoutApplicationVM`.  Zatím součástí soubor rd.xml pouze metadata direktiva je:  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 Kandidát pravděpodobnost selhání je, že `App.Core.ViewModels.Layout.LayoutApplicationVM` chybí metadata, protože se jiný obor názvů.  
  
 V takovém případě přidání direktivy modulu runtime pro `App.Core.ViewModels` vyřešení problému. Původní příčina volání rozhraní API k <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> metodu, která vrátila **null**, a aplikace tiše ignorováno problém, dokud došlo k chybě.  
  
 V dynamické programování, je vhodné při použití reflexe rozhraní API v rámci [!INCLUDE[net_native](../../../includes/net-native-md.md)] , je použít <xref:System.Type.GetType%2A?displayProperty=nameWithType> přetížení, které vyvolají výjimku při selhání.  
  
## <a name="is-this-an-isolated-case"></a>Je to izolované případu?  
 Další problémy mohou nastat také při použití `App.Core.ViewModels`.  Musíte se rozhodnout, zda je vhodné identifikace a opravuje chybějící výjimka metadat nebo šetří čas a přidání direktivy pro větší třídy typů.  Tady, přidání `dynamic` metadata pro `App.Core.ViewModels` může být nejlepším řešením, pokud výsledný nárůst velikosti výstupního binárního souboru není problém.  
  
## <a name="could-the-code-be-rewritten"></a>Může být přepsán kód?  
 Pokud aplikace použili `typeof(LayoutApplicationVM)` místo `Type.GetType("LayoutApplicationVM")`, může mít zachovány řetězce nástrojů `browse` metadat.  Ale je stále by vytvořili `invoke` metadat, které by vedly k [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) při vytváření instance typu došlo k výjimce. Aby se zabránilo výjimky, by stále musíte přidat direktivy modulu runtime pro obor názvů nebo typ, který určuje `dynamic` zásad. Informace o direktivy modulu runtime, najdete v článku [direktivy modulu Runtime (rd.xml) odkaz na soubor konfigurace](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="see-also"></a>Viz také:

- [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [Příklad: Zpracování výjimek při vázání dat](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
