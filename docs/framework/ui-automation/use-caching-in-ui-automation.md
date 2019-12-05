---
title: Použití mezipaměti při automatizaci uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: 679192b611a423e095ee9acc956d247364940edf
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800805"
---
# <a name="use-caching-in-ui-automation"></a>Použití mezipaměti při automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 V této části se dozvíte, jak implementovat ukládání do mezipaměti <xref:System.Windows.Automation.AutomationElement> vlastností a vzorů ovládacích prvků.  
  
### <a name="activate-a-cache-request"></a>Aktivace žádosti o mezipaměť  
  
1. Vytvoření <xref:System.Windows.Automation.CacheRequest>.  
  
2. Zadání vlastností a vzorů pro ukládání do mezipaměti pomocí <xref:System.Windows.Automation.CacheRequest.Add%2A>.  
  
3. Určete rozsah ukládání do mezipaměti nastavením vlastnosti <xref:System.Windows.Automation.CacheRequest.TreeScope%2A>.  
  
4. Určete zobrazení podstromu nastavením vlastnosti <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A>.  
  
5. Nastavte vlastnost <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> na <xref:System.Windows.Automation.AutomationElementMode.None>, pokud chcete zvýšit efektivitu tím, že nenačtete úplný odkaz na objekty. (Díky tomu nebude možné načíst aktuální hodnoty z těchto objektů.)  
  
6. Aktivujte žádost pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> v rámci bloku `using` (`Using` v Microsoft Visual Basic .NET).  
  
 Po získání <xref:System.Windows.Automation.AutomationElement> objektů nebo přihlášení k odběru událostí deaktivujte požadavek pomocí <xref:System.Windows.Automation.CacheRequest.Pop%2A> (Pokud se <xref:System.Windows.Automation.CacheRequest.Push%2A> použil), nebo odstraněním objektu vytvořeného <xref:System.Windows.Automation.CacheRequest.Activate%2A>. (Použijte <xref:System.Windows.Automation.CacheRequest.Activate%2A> v bloku `using` (`Using` v Microsoft Visual Basic .NET).  
  
### <a name="cache-automationelement-properties"></a>Vlastnosti třída AutomationElement neobsahuje mezipaměti  
  
1. Když je aktivní <xref:System.Windows.Automation.CacheRequest>, získat <xref:System.Windows.Automation.AutomationElement> objektů pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; nebo můžete získat <xref:System.Windows.Automation.AutomationElement> jako zdroj události, kterou jste zaregistrovali v případě, že byla <xref:System.Windows.Automation.CacheRequest> aktivní. (Mezipaměť můžete vytvořit také tak, že předáte <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache nebo jednu z <xref:System.Windows.Automation.TreeWalker> metod.)  
  
2. Použijte <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> nebo načtěte vlastnost z vlastnosti <xref:System.Windows.Automation.AutomationElement.Cached%2A> <xref:System.Windows.Automation.AutomationElement>.  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Získání vzorů v mezipaměti a jejich vlastností  
  
1. Když je aktivní <xref:System.Windows.Automation.CacheRequest>, získat <xref:System.Windows.Automation.AutomationElement> objektů pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; nebo můžete získat <xref:System.Windows.Automation.AutomationElement> jako zdroj události, kterou jste zaregistrovali v případě, že byla <xref:System.Windows.Automation.CacheRequest> aktivní. (Mezipaměť můžete vytvořit také tak, že předáte <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache nebo jednu z <xref:System.Windows.Automation.TreeWalker> metod.)  
  
2. K načtení vzoru uloženého v mezipaměti použijte <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>.  
  
3. Načte hodnoty vlastností z vlastnosti `Cached` vzoru ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> pro aktivaci <xref:System.Windows.Automation.CacheRequest>.  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti pomocí <xref:System.Windows.Automation.CacheRequest.Push%2A> pro aktivaci <xref:System.Windows.Automation.CacheRequest>. S výjimkou případů, kdy chcete vnořit požadavky do mezipaměti, je vhodnější použít <xref:System.Windows.Automation.CacheRequest.Activate%2A>.  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Viz také:

- [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](caching-in-ui-automation-clients.md)
