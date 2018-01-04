---
title: "Potíže s vlákny při automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
caps.latest.revision: "9"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9e5c38f5c4681210a4f3be552a3f08be3962bc2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-threading-issues"></a>Potíže s vlákny při automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Z důvodu způsob [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] používá zpráv systému Windows, je v konfliktu může dojít, když klientské aplikace pokusí o interakci s vlastním [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken. Tyto konflikty může vést k velmi nízký výkon nebo i způsobit, že aplikace přestane reagovat.  
  
 Pokud klientské aplikace slouží k interakci se všechny elementy na ploše, včetně vlastní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], měli byste si všechny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] volání na samostatné vlákno. To zahrnuje vyhledání elementy (například pomocí <xref:System.Windows.Automation.TreeWalker> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metoda) a pomocí vzorů ovládacích prvků.  
  
 Je bezpečné, aby [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] volá v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obslužné rutiny události, protože obslužná rutina události je volána vždy na jinou hodnotu než[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken. Ale při přihlášení k odběru událostí, které mohou pocházet z klientské aplikace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], je třeba volání <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, nebo související metody, na jinou hodnotu než[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken. Obslužné rutiny událostí ve stejném vlákně, odeberte.
