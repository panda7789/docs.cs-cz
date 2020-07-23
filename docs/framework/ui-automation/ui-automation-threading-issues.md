---
title: Potíže s vlákny při automatizaci uživatelského rozhraní
description: Přečtěte si o problémech s vlákny automatizace uživatelského rozhraní. Konflikty mohou nastat například v případě, že se klientská aplikace pokusí pracovat s vlastním uživatelským rozhraním ve vlákně uživatelského rozhraní.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: 290c26981d5eb993e2a9ab387f8d106aafa54efb
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924536"
---
# <a name="ui-automation-threading-issues"></a>Potíže s vlákny při automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Z důvodu způsobu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] použití zpráv systému Windows může dojít ke konfliktům, pokud se klientská aplikace pokusí o interakci s vlastním [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vláknem. Tyto konflikty mohou vést k velmi pomalému výkonu nebo dokonce způsobit, že aplikace přestane reagovat.  
  
 Pokud je vaše klientská aplikace určena pro interakci se všemi prvky na ploše, včetně vlastní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , měli byste všechna volání provést [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v samostatném vlákně. To zahrnuje vyhledání prvků (například pomocí <xref:System.Windows.Automation.TreeWalker> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metody nebo metody) a používání vzorů ovládacích prvků.  
  
 Je bezpečné volat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obslužné rutiny události, protože obslužná rutina události je vždy volána v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] nevlákně. Pokud se však přihlašujete k odběru událostí, které mohou být vytvořeny z klientské aplikace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , je nutné provést volání <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A> nebo související metodu na jiné než [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vlákně. Odeberte obslužné rutiny událostí ve stejném vlákně.
