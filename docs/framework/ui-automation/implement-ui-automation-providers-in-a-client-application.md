---
title: "Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích"
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
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
caps.latest.revision: "6"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: ae7b478ec8d836f1e0772d81185b9bb0119c0fa8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje ukázkový kód, který ukazuje, jak pro implementaci zprostředkovatele automatizace uživatelského rozhraní na straně klienta v rámci aplikace.  
  
 Jedná se o scénář neobvyklé. Automatizace uživatelského rozhraní klientské aplikace nejčastěji využívá zprostředkovatele na straně serveru nebo zprostředkovatele na straně klienta, které se nacházejí v knihovně DLL.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu implementuje jednoduchého zprostředkovatele okna konzoly. Kód nemá žádné užitečné funkce, ale je určená k předvedení základní kroky v nastavení služby zprostředkovatele v rámci kód klienta a její registrací pomocí <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled zprostředkovatelů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [Registrace sestavení zprostředkovatele na straně klienta](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)  
 [Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)  
 [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
