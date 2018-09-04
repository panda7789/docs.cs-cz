---
title: Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: d627b415c0530de4957b663869c74b762421a35c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509942"
---
# <a name="raise-events-from-a-ui-automation-provider"></a>Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje ukázkový kód, který ukazuje, jak vyvolat událost ze zprostředkovatele automatizace uživatelského rozhraní.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událost je aktivována při provádění vlastního ovládacího prvku. Implementace umožňuje klientské aplikaci automatizace uživatelského rozhraní pro simulaci klikněte na tlačítko.  
  
 Aby nedocházelo k zbytečné zpracování kontroluje v příkladu <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> chcete zobrazit, zda by měla být zvýšena události.  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled zprostředkovatelů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
