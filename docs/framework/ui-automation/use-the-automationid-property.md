---
title: Používání vlastnosti AutomationID
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
ms.openlocfilehash: 1699d39f5f456fe08b043e5b6a687d4c59d28e89
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040343"
---
# <a name="use-the-automationid-property"></a>Používání vlastnosti AutomationID
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje scénáře a vzorový kód, který ukazuje, jak a <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> kdy lze použít k vyhledání elementu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v rámci stromu.  
  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>jednoznačně identifikuje prvek automatizace uživatelského rozhraní z jeho položek na stejné úrovni. Další informace o identifikátorech vlastností souvisejících s identifikací ovládacích prvků najdete v tématu [Přehled vlastností automatizace uživatelského rozhraní](ui-automation-properties-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>nezaručuje jedinečnou identitu v celém stromu. obvykle potřebují informace o kontejneru a oboru, aby byly užitečné. Například aplikace může obsahovat ovládací prvek nabídky s více položkami nabídky nejvyšší úrovně, které zase mají více podřízených položek nabídky. Tyto sekundární položky nabídky mohou být identifikovány pomocí obecného schématu, jako je "Item1 –", "položka 2" atd., což povoluje duplicitní identifikátory pro podřízené položky v rámci položek nabídky nejvyšší úrovně.  
  
## <a name="scenarios"></a>Scénáře  
 Zjistili jsme tři primární scénáře klientské aplikace automatizace uživatelského rozhraní, které vyžadují použití <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> k dosažení přesného a konzistentního výsledku při hledání prvků.  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>je podporováno všemi prvky automatizace uživatelského rozhraní v zobrazení ovládacích prvků kromě oken aplikace nejvyšší úrovně, prvky automatizace uživatelského rozhraní odvozené z [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ovládacích prvků, které nemají identifikátor nebo x:UID –, a prvky automatizace uživatelského rozhraní odvozené z [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] ovládacích prvků, které nemáte ID ovládacího prvku.  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a>Použití jedinečného a zjistitelného AutomationID k vyhledání konkrétního prvku ve stromu automatizace uživatelského rozhraní  
  
- Použijte nástroj [!INCLUDE[TLA#tla_uispy](../../../includes/tlasharptla-uispy-md.md)] , jako je například, k <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> hlášení [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvku zájmu. Tuto hodnotu lze následně zkopírovat a vložit do klientské aplikace, jako je například testovací skript pro následné automatizované testování. Tento přístup snižuje a zjednodušuje kód nezbytný k identifikaci a vyhledání prvku za běhu.  
  
> [!CAUTION]
> Obecně byste se měli pokusit získat pouze přímé podřízené objekty <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Hledání potomků může iterovat stovky nebo dokonce tisíce prvků, což může způsobit přetečení zásobníku. Pokud se pokoušíte získat konkrétní prvek na nižší úrovni, měli byste zahájit hledání z okna aplikace nebo z kontejneru na nižší úrovni.  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a>Pro návrat k dříve identifikovanému třída AutomationElement neobsahuje použijte trvalou cestu.  
  
- Klientské aplikace, od jednoduchých testovacích skriptů až po robustní nástroje pro nahrávání a přehrávání, můžou vyžadovat přístup k elementům, které nejsou aktuálně vytvořeny instance, jako je otevření dialogového okna nebo položka nabídky, a proto neexistují ve stromu automatizace uživatelského rozhraní. Na tyto prvky lze vytvořit instanci pouze pomocí reprodukce nebo přehrání, konkrétní sekvence akcí uživatelského rozhraní prostřednictvím použití vlastností automatizace uživatelského rozhraní, jako jsou AutomationID, vzory ovládacích prvků a naslouchací procesy událostí.
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a>Pro návrat k dříve identifikovanému třída AutomationElement neobsahuje použijte relativní cestu  
  
- V některých případech, protože AutomationID je zaručená jenom jedinečnost mezi členy na stejné úrovni, může mít více elementů ve stromu automatizace uživatelského rozhraní stejné hodnoty vlastností AutomationID. V těchto situacích mohou být prvky jednoznačně identifikovány na základě nadřazené položky a v případě potřeby i prarodič. Například vývojář může poskytnout řádek nabídek s více položkami nabídky každý s více položkami nabídky, kde jsou identifikovány pomocí sekvenčního AutomationID, jako je například "Item1 –", "Item2" atd. Jednotlivé položky nabídky by pak mohly být jedinečně identifikovány svými AutomationIDy spolu s AutomationID svého nadřazeného prvku a v případě potřeby jeho prarodičem.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost](find-a-ui-automation-element-based-on-a-property-condition.md)
