---
title: Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: a60253e62f814e9e3ea7ed4c5720e98e470d7f79
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043595"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje příklad kódu, který ukazuje, jak implementovat zprostředkovatele automatizace uživatelského rozhraní na straně klienta v rámci aplikace.  
  
 Toto je neobvyklý scénář. Nejčastěji se klientská aplikace automatizace uživatelského rozhraní používá pro poskytovatele na straně serveru nebo poskytovatele na straně klienta, kteří se nacházejí v knihovně DLL.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu implementuje jednoduchého poskytovatele pro okno konzoly. Kód nemá žádné užitečné funkce, ale je určen k předvedení základních kroků při nastavování poskytovatele v rámci kódu klienta a jeho registraci pomocí <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled zprostředkovatelů automatizace uživatelského rozhraní](ui-automation-providers-overview.md)
- [Registrace sestavení zprostředkovatele na straně klienta](register-a-client-side-provider-assembly.md)
- [Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta](create-a-client-side-ui-automation-provider.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta](client-side-ui-automation-provider-implementation.md)
