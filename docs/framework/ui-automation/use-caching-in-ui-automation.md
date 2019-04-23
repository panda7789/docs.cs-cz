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
ms.openlocfilehash: b63d94789d081ce7337b5f9c2abca3f7d9e99eeb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308663"
---
# <a name="use-caching-in-ui-automation"></a>Použití mezipaměti při automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tato část ukazuje, jak implementovat ukládání do mezipaměti <xref:System.Windows.Automation.AutomationElement> vzory vlastností a ovládacího prvku.  
  
### <a name="activate-a-cache-request"></a>Aktivovat žádost o mezipaměti  
  
1. Vytvoření <xref:System.Windows.Automation.CacheRequest>.  
  
2. Zadejte vlastnosti a vzorce do mezipaměti pomocí <xref:System.Windows.Automation.CacheRequest.Add%2A>.  
  
3. Zadejte rozsah ukládání do mezipaměti tak, že nastavíte <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> vlastnost.  
  
4. Určete zobrazení podstrom nastavením <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> vlastnost.  
  
5. Nastavte <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> vlastnost <xref:System.Windows.Automation.AutomationElementMode.None> Pokud chcete zvýšit efektivitu nenačítání úplný odkaz na objekty. (To znamená, že není možné načíst aktuální hodnoty z těchto objektů.)  
  
6. Aktivovat žádost pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> v rámci `using` blok (`Using` v aplikaci Microsoft Visual Basic .NET).  
  
 Po získání <xref:System.Windows.Automation.AutomationElement> objekty nebo přihlášení k odběru událostí, deaktivovat žádost pomocí <xref:System.Windows.Automation.CacheRequest.Pop%2A> (Pokud <xref:System.Windows.Automation.CacheRequest.Push%2A> byla použita) nebo uvolnění objektu vytvořeného <xref:System.Windows.Automation.CacheRequest.Activate%2A>. (Použití <xref:System.Windows.Automation.CacheRequest.Activate%2A> v `using` blok (`Using` v aplikaci Microsoft Visual Basic .NET).  
  
### <a name="cache-automationelement-properties"></a>Třída AutomationElement vlastnosti mezipaměti  
  
1. Zatímco <xref:System.Windows.Automation.CacheRequest> je aktivní, získat <xref:System.Windows.Automation.AutomationElement> objektů pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; nebo získat <xref:System.Windows.Automation.AutomationElement> jako zdroj události, které jste zaregistrovali pro případ <xref:System.Windows.Automation.CacheRequest> byl aktivní. (Můžete také vytvořit mezipaměť předáním <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache nebo jeden z <xref:System.Windows.Automation.TreeWalker> metody.)  
  
2. Použití <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> nebo načtení vlastnosti z <xref:System.Windows.Automation.AutomationElement.Cached%2A> vlastnost <xref:System.Windows.Automation.AutomationElement>.  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Získat vzory v mezipaměti a jejich vlastnosti  
  
1. Zatímco <xref:System.Windows.Automation.CacheRequest> je aktivní, získat <xref:System.Windows.Automation.AutomationElement> objektů pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; nebo získat <xref:System.Windows.Automation.AutomationElement> jako zdroj události, které jste zaregistrovali pro případ <xref:System.Windows.Automation.CacheRequest> byl aktivní. (Můžete také vytvořit mezipaměť předáním <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache nebo jeden z <xref:System.Windows.Automation.TreeWalker> metody.)  
  
2. Použití <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> načíst vzor uložený v mezipaměti.  
  
3. Načíst hodnoty vlastností z `Cached` vlastnost vzor ovládacích prvků.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti, pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> aktivovat <xref:System.Windows.Automation.CacheRequest>.  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti, pomocí <xref:System.Windows.Automation.CacheRequest.Push%2A> aktivovat <xref:System.Windows.Automation.CacheRequest>. S výjimkou toho, když budete chtít vnořit požadavků mezipaměti, je vhodnější použít <xref:System.Windows.Automation.CacheRequest.Activate%2A>.  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Viz také:

- [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
