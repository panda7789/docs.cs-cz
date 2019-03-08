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
ms.openlocfilehash: 102a2fe1cb2598078af7246d5f88df928064693f
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676639"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje ukázkový kód, který ukazuje, jak pro implementaci zprostředkovatele automatizace uživatelského rozhraní na straně klienta v rámci aplikace.  
  
 To je běžné scénáře. Automatizace uživatelského rozhraní klientské aplikace nejčastěji využívá zprostředkovatele na straně serveru nebo zprostředkovatele na straně klienta, které jsou umístěny v knihovně DLL.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu implementuje jednoduchého zprostředkovatele pro okno konzoly. Kód nemá žádné užitečných funkcí, ale je za cíl předvést základní kroky při vytváření poskytovatele v rámci kódu klienta a její registrací pomocí <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled zprostředkovatelů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Registrace sestavení zprostředkovatele na straně klienta](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
- [Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
