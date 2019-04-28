---
title: 'Postupy: Registrace přidružené vlastnosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
ms.openlocfilehash: 4c678a64b62b8f4db24cf39ffbafac52e56c9982
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768677"
---
# <a name="how-to-register-an-attached-property"></a>Postupy: Registrace přidružené vlastnosti
Tento příklad ukazuje, jak registrace připojené vlastnosti a zadejte veřejnou přistupující objekty tak, aby vlastnost můžete použít v obou [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a kódu. Připojené vlastnosti jsou koncept syntaxi definované [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Většina přidružené vlastnosti pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typy jsou také implementovány jako vlastnosti závislosti. Vlastnosti závislostí lze použít na jakémkoli <xref:System.Windows.DependencyObject> typy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak registrace připojené vlastnosti jako vlastnost závislosti, s použitím <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody. Třída zprostředkovatele má možnost poskytnout výchozí metadat pro vlastnost, která lze použít při vlastnost se používá na jiné třídy, pokud tuto třídu přepisuje metadata. V tomto příkladu, výchozí hodnota `IsBubbleSource` je nastavena na `false`.  
  
 Třída zprostředkovatele pro připojené vlastnosti (i když není registrován jako vlastnost závislosti) musí poskytnout statické get a set přistupující objekty, které podle konvence `Set` *[AttachedPropertyName]* a `Get` *[AttachedPropertyName]*. Tyto přístupové objekty jsou vyžadovány tak, aby jednající [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] čtečky dokáže rozpoznat vlastnost jako atribut v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a vyřešení příslušných typů.  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.DependencyProperty>
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Témata s postupy](properties-how-to-topics.md)
