---
title: 'Příklad: Řešení potíží s dynamickým programováním'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
ms.openlocfilehash: ff179854066d024a89cb5a84a19d0b9bb054d6e5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128444"
---
# <a name="example-troubleshooting-dynamic-programming"></a>Příklad: Řešení potíží s dynamickým programováním
> [!NOTE]
> Toto téma se týká .NET Native Developer Preview, což je předběžná verze softwaru. Verzi Preview si můžete stáhnout z [webu Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).  
  
 Ne všechna selhání při vyhledávání metadat v aplikacích vyvinutých pomocí řetězu nástrojů .NET Native způsobily výjimku.  Některé mohou v aplikaci v nepředvídatelných způsobech manifestovat.  Následující příklad ukazuje narušení přístupu způsobené odkazem na objekt s hodnotou null:  
  
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
  
 Pojďme se pokusit tuto výjimku vyřešit pomocí třech kroků popsaných v části "Ruční řešení chybějících metadat" v [Začínáme](getting-started-with-net-native.md).  
  
## <a name="what-was-the-app-doing"></a>Co aplikace právě dělala?  
 První věcí, kterou je třeba poznamenat, je klíčové slovo, které je `async` základem zásobníku.  Určení toho, co aplikace skutečně prováděla v `async` metodě může být problematické, protože zásobník ztratil kontext původního volání a spustil `async` kód v jiném vlákně. Můžeme ale odvodit, že se aplikace pokouší načíst první stránku.  V implementaci pro `NavigationArgs.Setup` , následující kód způsobil porušení přístupu:  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 V této instanci `LayoutVM` vlastnost `AppViewModel.Current` měla **hodnotu null**.  Některé z absencí metadat způsobily malý rozdíl v chování a způsobily neinicializované vlastnosti namísto set, jak očekává aplikace.  Nastavení zarážky v kódu, kde `LayoutVM` by mělo být inicializováno, může vyvolat světlo v situaci.  Upozorňujeme však, že `LayoutVM` typ je `App.Core.ViewModels.Layout.LayoutApplicationVM` .  V souboru Rd. XML je zatím přítomna jediná direktiva metadat:  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 Pravděpodobným kandidátem na selhání je, že `App.Core.ViewModels.Layout.LayoutApplicationVM` metadata chybí, protože se nacházejí v jiném oboru názvů.  
  
 V tomto případě přidejte direktivu modulu runtime pro `App.Core.ViewModels` vyřešení problému. Hlavní příčinou bylo volání rozhraní API k <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> metodě, která vrátila **hodnotu null**, a aplikace tiše problém ignorovala, dokud nedošlo k chybě.  
  
 V dynamickém programování je vhodný postup při použití rozhraní API pro reflexi v rámci .NET Native použít <xref:System.Type.GetType%2A?displayProperty=nameWithType> přetížení, které vyvolávají výjimku při selhání.  
  
## <a name="is-this-an-isolated-case"></a>Jedná se o izolovaný případ?  
 K dalším potížím může dojít také při použití `App.Core.ViewModels` .  Je nutné rozhodnout, zda má být identifikována a opravena chybějící výjimka metadat, nebo ušetřit čas a přidat direktivy pro větší třídu typů.  Tady je přidání `dynamic` metadat pro `App.Core.ViewModels` může být nejlepší přístup, pokud výsledná velikost výstupního binárního souboru není problémem.  
  
## <a name="could-the-code-be-rewritten"></a>Byl kód přepsán?  
 Pokud se `typeof(LayoutApplicationVM)` místo toho použila aplikace `Type.GetType("LayoutApplicationVM")` , řetězec nástroje by mohl uchovávat `browse` metadata.  Přesto však nevytvořila `invoke` metadata, což by vedlo k výjimce [MissingMetadataException](missingmetadataexception-class-net-native.md) při vytváření instance typu. Chcete-li zabránit výjimce, je stále nutné přidat direktivu modulu runtime pro obor názvů nebo typ, který určuje `dynamic` zásadu. Informace o direktivách modulu runtime naleznete v tématu [reference ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="see-also"></a>Viz také

- [Začínáme](getting-started-with-net-native.md)
- [Příklad: Zpracování výjimek při vázání dat](example-handling-exceptions-when-binding-data.md)
