---
title: Potíže s vlákny při automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: 8dc21a680a19933e9db8d52a0e6b7e6ffdd333f8
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800827"
---
# <a name="ui-automation-threading-issues"></a>Potíže s vlákny při automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Kvůli způsobu, jakým [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] používá zprávy systému Windows, může dojít ke konfliktům, pokud se klientská aplikace pokusí o interakci s vlastním [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na vlákně [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Tyto konflikty mohou vést k velmi pomalému výkonu nebo dokonce způsobit, že aplikace přestane reagovat.  
  
 Pokud je vaše klientská aplikace určena pro interakci se všemi prvky na ploše, včetně vlastní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], měli byste provést všechna [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] volání v samostatném vlákně. To zahrnuje vyhledání prvků (například pomocí <xref:System.Windows.Automation.TreeWalker> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metody) a použití vzorů ovládacích prvků.  
  
 Je bezpečné zajistit [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] volání v rámci obslužné rutiny události [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], protože obslužná rutina události je vždy volána v ne[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]m vlákně. Pokud se však přihlašujete k odběru událostí, které mohou pocházet z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]klientské aplikace, je nutné provést volání <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>nebo související metodu v ne[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vlákně. Odeberte obslužné rutiny událostí ve stejném vlákně.
