---
title: Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích
description: Podívejte se na příklad implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta v aplikaci. Všimněte si, že se jedná o neobvyklý scénář.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: c604b68021886abdf06360bfb8afefe3640c12fe
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164124"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje příklad kódu, který ukazuje, jak implementovat zprostředkovatele automatizace uživatelského rozhraní na straně klienta v rámci aplikace.  
  
 Toto je neobvyklý scénář. Nejčastěji se klientská aplikace automatizace uživatelského rozhraní používá pro poskytovatele na straně serveru nebo poskytovatele na straně klienta, kteří se nacházejí v knihovně DLL.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu implementuje jednoduchého poskytovatele pro okno konzoly. Kód nemá žádné užitečné funkce, ale je určen k předvedení základních kroků při nastavování poskytovatele v rámci kódu klienta a jeho registraci pomocí <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A> .  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Viz také

- [Přehled zprostředkovatelů automatizace uživatelského rozhraní](ui-automation-providers-overview.md)
- [Registrace sestavení zprostředkovatele na straně klienta](register-a-client-side-provider-assembly.md)
- [Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta](create-a-client-side-ui-automation-provider.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta](client-side-ui-automation-provider-implementation.md)
