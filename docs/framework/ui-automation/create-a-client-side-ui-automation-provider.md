---
title: Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta
description: Podívejte se na příklad vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta. Příklad implementuje jednoduchého poskytovatele na straně klienta pro okno konzoly.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
ms.openlocfilehash: a25966d0f11e409bd4e53f944fc2528360327039
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168478"
---
# <a name="create-a-client-side-ui-automation-provider"></a>Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje příklad kódu, který ukazuje, jak implementovat zprostředkovatele automatizace uživatelského rozhraní na straně klienta.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu lze integrovat do dynamické knihovny (DLL), která implementuje velmi jednoduchého poskytovatele na straně klienta pro okno konzoly. Kód nemá žádné užitečné funkce, ale je určen k předvedení základních kroků v nastavení sestavení zprostředkovatele, které lze registrovat pomocí klientské aplikace automatizace uživatelského rozhraní.  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a>Viz také

- [Přehled zprostředkovatelů automatizace uživatelského rozhraní](ui-automation-providers-overview.md)
- [Registrace sestavení zprostředkovatele na straně klienta](register-a-client-side-provider-assembly.md)
