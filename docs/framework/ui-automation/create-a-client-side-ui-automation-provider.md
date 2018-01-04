---
title: "Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6b788d679d29a9af838b91c7b4468e10a1a8411e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="create-a-client-side-ui-automation-provider"></a>Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje ukázkový kód, který ukazuje implementaci zprostředkovatele automatizace uživatelského rozhraní na straně klienta.  
  
## <a name="example"></a>Příklad  
 Může být součástí následující příklad kódu [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] velmi jednoduché zprostředkovatele na straně klienta pro okno konzoly, která implementuje. Kód nemá žádné užitečné funkce, ale je určená k předvedení základní kroky nastavení služby zprostředkovatele sestavení, které lze registrovat pomocí automatizace uživatelského rozhraní klientské aplikace.  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled zprostředkovatelů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [Registrace sestavení zprostředkovatele na straně klienta](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
