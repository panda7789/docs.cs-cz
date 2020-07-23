---
title: Použití mezipaměti při automatizaci uživatelského rozhraní
description: Podívejte se, jak používat ukládání do mezipaměti v automatizaci uživatelského rozhraní. Projděte si kroky pro aktivaci žádosti o mezipaměť, ukládání do mezipaměti třída AutomationElement neobsahuje vlastností a získání vzorů v mezipaměti.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: 8dff9db77e39dc66a16b6a7b395c76a3c768d48e
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924484"
---
# <a name="use-caching-in-ui-automation"></a>Použití mezipaměti při automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 V této části se dozvíte, jak implementovat ukládání <xref:System.Windows.Automation.AutomationElement> vlastností a vzorů ovládacích prvků do mezipaměti.  
  
### <a name="activate-a-cache-request"></a>Aktivace žádosti o mezipaměť  
  
1. Vytvořte <xref:System.Windows.Automation.CacheRequest> .  
  
2. Zadejte vlastnosti a vzory pro ukládání do mezipaměti pomocí <xref:System.Windows.Automation.CacheRequest.Add%2A> .  
  
3. Určete rozsah ukládání do mezipaměti nastavením <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> Vlastnosti.  
  
4. Určete zobrazení podstromu nastavením <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> Vlastnosti.  
  
5. Nastavte <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> vlastnost na hodnotu, <xref:System.Windows.Automation.AutomationElementMode.None> Pokud chcete zvýšit efektivitu tím, že nenačtete úplný odkaz na objekty. (Díky tomu nebude možné načíst aktuální hodnoty z těchto objektů.)  
  
6. Aktivujte žádost pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` bloku ( `Using` v Microsoft Visual Basic .NET).  
  
 Po získání <xref:System.Windows.Automation.AutomationElement> objektů nebo přihlášení k odběru událostí dezaktivujte požadavek pomocí <xref:System.Windows.Automation.CacheRequest.Pop%2A> (Pokud <xref:System.Windows.Automation.CacheRequest.Push%2A> bylo použito) nebo likvidací objektu vytvořeného pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> . (Použijte <xref:System.Windows.Automation.CacheRequest.Activate%2A> v `using` bloku ( `Using` v Microsoft Visual Basic .NET).  
  
### <a name="cache-automationelement-properties"></a>Vlastnosti třída AutomationElement neobsahuje mezipaměti  
  
1. Když <xref:System.Windows.Automation.CacheRequest> je aktivní, získá <xref:System.Windows.Automation.AutomationElement> objekty pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ; nebo získá <xref:System.Windows.Automation.AutomationElement> jako zdroj události, kterou jste zaregistrovali v okamžiku, kdy <xref:System.Windows.Automation.CacheRequest> byla aktivní. (Mezipaměť můžete vytvořit také předáním <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache nebo jedné z <xref:System.Windows.Automation.TreeWalker> metod.)  
  
2. Použijte <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> nebo načtěte vlastnost z <xref:System.Windows.Automation.AutomationElement.Cached%2A> vlastnosti <xref:System.Windows.Automation.AutomationElement> .  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Získání vzorů v mezipaměti a jejich vlastností  
  
1. Když <xref:System.Windows.Automation.CacheRequest> je aktivní, získá <xref:System.Windows.Automation.AutomationElement> objekty pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ; nebo získá <xref:System.Windows.Automation.AutomationElement> jako zdroj události, kterou jste zaregistrovali v okamžiku, kdy <xref:System.Windows.Automation.CacheRequest> byla aktivní. (Mezipaměť můžete vytvořit také předáním <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache nebo jedné z <xref:System.Windows.Automation.TreeWalker> metod.)  
  
2. Použijte <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> k načtení vzoru uloženého v mezipaměti.  
  
3. Načte hodnoty vlastností z `Cached` vlastnosti vzoru ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti pomocí nástroje <xref:System.Windows.Automation.CacheRequest.Activate%2A> pro aktivaci <xref:System.Windows.Automation.CacheRequest> .  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti pomocí nástroje <xref:System.Windows.Automation.CacheRequest.Push%2A> pro aktivaci <xref:System.Windows.Automation.CacheRequest> . S výjimkou případů, kdy chcete vnořit požadavky do mezipaměti, je vhodnější použít <xref:System.Windows.Automation.CacheRequest.Activate%2A> .  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Viz také

- [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](caching-in-ui-automation-clients.md)
