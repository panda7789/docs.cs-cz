---
title: 'Postupy: Implementace ověření připojení'
description: Naučte se používat ověřování vazby k poskytnutí vizuální zpětné vazby uživateli, když je v Windows Presentation Foundation (WPF) zadána neplatná hodnota.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 0813be9f79a83a9dae26db1dadb58b5e973339fd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617879"
---
# <a name="how-to-implement-binding-validation"></a>Postupy: Implementace ověření připojení

Tento příklad ukazuje, jak použít <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> aktivační proceduru a se stylem k poskytnutí vizuální zpětné vazby, která uživatele informují o tom, že je zadána neplatná hodnota na základě vlastního ověřovacího pravidla.

## <a name="example"></a>Příklad

Textový obsah <xref:System.Windows.Controls.TextBox> v následujícím příkladu je vázán na `Age` vlastnost (typu int) objektu zdroje vazby s názvem `ods` . Vazba je nastavená tak, aby používala ověřovací pravidlo s názvem `AgeRangeRule` , aby pokud uživatel zadal jiné než číselné znaky nebo hodnotu menší než 21 nebo větší než 130, zobrazí se vedle textového pole červený vykřičník a v případě, že uživatel přesune ukazatel myši na textové pole, zobrazí se chybová zpráva s chybovou zprávou.

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

Následující příklad ukazuje implementaci `AgeRangeRule` , která dědí z <xref:System.Windows.Controls.ValidationRule> a Přepisuje <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodu. `Int32.Parse`Metoda je volána na hodnotu, aby se zajistilo, že neobsahuje neplatné znaky. <xref:System.Windows.Controls.ValidationRule.Validate%2A>Metoda vrátí hodnotu <xref:System.Windows.Controls.ValidationResult> , která označuje, zda je hodnota platná na základě toho, zda je při analýze zachycena výjimka a zda je hodnota stáří mimo dolní a horní mez.

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

Následující příklad ukazuje vlastní <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` , který vytvoří červený vykřičník pro upozornění uživatele na chybu ověřování. Šablony ovládacích prvků slouží k předefinování vzhledu ovládacího prvku.

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

Jak je znázorněno v následujícím příkladu, <xref:System.Windows.Controls.ToolTip> zobrazuje se chybová zpráva, která je vytvořena pomocí stylu s názvem `textBoxInError` . Pokud <xref:System.Windows.Controls.Validation.HasError%2A> je hodnota `true` , aktivační událost nastaví popisek nástroje aktuální <xref:System.Windows.Controls.TextBox> na jeho první chybu ověření. <xref:System.Windows.Data.Binding.RelativeSource%2A>Je nastaven na <xref:System.Windows.Data.RelativeSourceMode.Self> a odkazuje na aktuální prvek.

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

Úplný příklad najdete v tématu [Ukázka ověření vazby](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).
  
Všimněte si, že pokud neposkytnete vlastní <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> výchozí šablonu chyb, zobrazí se uživateli při chybě ověření vizuální zpětná vazba. Další informace najdete v tématu věnovaném ověření dat v [přehledu datových vazeb](../../../desktop-wpf/data/data-binding-overview.md) . Také [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje integrované ověřovací pravidlo, které zachycuje výjimky, které jsou vyvolány během aktualizace vlastnosti zdroje vazby. Další informace naleznete v tématu <xref:System.Windows.Controls.ExceptionValidationRule>.

## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [– postupy](data-binding-how-to-topics.md)
