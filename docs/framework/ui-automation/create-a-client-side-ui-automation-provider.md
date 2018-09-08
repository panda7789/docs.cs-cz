---
title: Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 8763277052a15e7cde1a5b03e124551bc91328df
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44181508"
---
# <a name="create-a-client-side-ui-automation-provider"></a>Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje ukázkový kód, který ukazuje, jak pro implementaci zprostředkovatele automatizace uživatelského rozhraní na straně klienta.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu může být integrovaná [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] , který implementuje velmi jednoduchého zprostředkovatele na straně klienta pro okno konzoly. Kód nemá žádné užitečných funkcí, ale je za cíl předvést základní kroky obsažené v nastavení poskytovatele sestavení, které lze registrovat pomocí automatizace uživatelského rozhraní klientské aplikace.  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled zprostředkovatelů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [Registrace sestavení zprostředkovatele na straně klienta](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
