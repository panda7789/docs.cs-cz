---
title: Potíže s vlákny při automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: f4820d2db6275e3c1ae9b55754b8cb6fec6fcc56
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954052"
---
# <a name="ui-automation-threading-issues"></a>Potíže s vlákny při automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Z důvodu způsobu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] použití zpráv systému Windows může dojít ke konfliktům, pokud se klientská aplikace pokusí o interakci [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] s vlastním [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vláknem. Tyto konflikty mohou vést k velmi pomalému výkonu nebo dokonce způsobit, že aplikace přestane reagovat.  
  
 Pokud je vaše klientská aplikace určena pro interakci se všemi prvky na ploše, včetně [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]vlastní, měli byste všechna [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] volání provést v samostatném vlákně. To zahrnuje vyhledání prvků (například pomocí <xref:System.Windows.Automation.TreeWalker> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metody nebo metody) a používání vzorů ovládacích prvků.  
  
 Je bezpečné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] volat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v rámci obslužné rutiny události, protože obslužná rutina události je vždy[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] volána v nevlákně. Pokud se však přihlašujete k odběru událostí, které mohou být vytvořeny z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]klientské aplikace, je nutné provést <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>volání nebo související metodu na jiné než[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vlákně. Odeberte obslužné rutiny událostí ve stejném vlákně.
