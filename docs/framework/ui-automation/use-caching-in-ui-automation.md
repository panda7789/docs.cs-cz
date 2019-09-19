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
ms.openlocfilehash: dd7506d388ba215f671ee3c7c4bae09baf4cc2b3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040313"
---
# <a name="use-caching-in-ui-automation"></a>Použití mezipaměti při automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 V této části se dozvíte, jak <xref:System.Windows.Automation.AutomationElement> implementovat ukládání vlastností a vzorů ovládacích prvků do mezipaměti.  
  
### <a name="activate-a-cache-request"></a>Aktivace žádosti o mezipaměť  
  
1. Vytvoření <xref:System.Windows.Automation.CacheRequest>.  
  
2. Zadejte vlastnosti a vzory pro ukládání do mezipaměti <xref:System.Windows.Automation.CacheRequest.Add%2A>pomocí.  
  
3. Určete rozsah ukládání do mezipaměti <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> nastavením vlastnosti.  
  
4. Určete zobrazení podstromu <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> nastavením vlastnosti.  
  
5. Nastavte vlastnost na <xref:System.Windows.Automation.AutomationElementMode.None> hodnotu, pokud chcete zvýšit efektivitu tím, že nenačtete úplný odkaz na objekty. <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> (Díky tomu nebude možné načíst aktuální hodnoty z těchto objektů.)  
  
6. Aktivujte žádost pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` bloku (`Using` v Microsoft Visual Basic .NET).  
  
 Po získání <xref:System.Windows.Automation.AutomationElement> objektů nebo přihlášení k odběru událostí dezaktivujte požadavek pomocí <xref:System.Windows.Automation.CacheRequest.Pop%2A> (Pokud <xref:System.Windows.Automation.CacheRequest.Push%2A> bylo použito) nebo likvidací objektu vytvořeného pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A>. (Použijte <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` v bloku (`Using` v Microsoft Visual Basic .NET).  
  
### <a name="cache-automationelement-properties"></a>Vlastnosti třída AutomationElement neobsahuje mezipaměti  
  
1. <xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement> Když je aktivní, získá <xref:System.Windows.Automation.AutomationElement> objekty pomocí nebo; nebo získá jako zdroj události, kterou jste zaregistrovali v okamžiku, kdy <xref:System.Windows.Automation.CacheRequest> byla aktivní. <xref:System.Windows.Automation.CacheRequest> (Mezipaměť můžete vytvořit také předáním <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache nebo jedné <xref:System.Windows.Automation.TreeWalker> z metod.)  
  
2. Použijte <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> nebo načtěte vlastnost <xref:System.Windows.Automation.AutomationElement.Cached%2A> z vlastnosti <xref:System.Windows.Automation.AutomationElement>.  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Získání vzorů v mezipaměti a jejich vlastností  
  
1. <xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement> Když je aktivní, získá <xref:System.Windows.Automation.AutomationElement> objekty pomocí nebo; nebo získá jako zdroj události, kterou jste zaregistrovali v okamžiku, kdy <xref:System.Windows.Automation.CacheRequest> byla aktivní. <xref:System.Windows.Automation.CacheRequest> (Mezipaměť můžete vytvořit také předáním <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache nebo jedné <xref:System.Windows.Automation.TreeWalker> z metod.)  
  
2. Použijte <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo<xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> k načtení vzoru uloženého v mezipaměti.  
  
3. Načte hodnoty vlastností z `Cached` vlastnosti vzoru ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti pomocí nástroje <xref:System.Windows.Automation.CacheRequest.Activate%2A> pro <xref:System.Windows.Automation.CacheRequest>aktivaci.  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti pomocí nástroje <xref:System.Windows.Automation.CacheRequest.Push%2A> pro <xref:System.Windows.Automation.CacheRequest>aktivaci. S výjimkou případů, kdy chcete vnořit požadavky do mezipaměti, je vhodnější použít <xref:System.Windows.Automation.CacheRequest.Activate%2A>.  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Viz také:

- [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](caching-in-ui-automation-clients.md)
