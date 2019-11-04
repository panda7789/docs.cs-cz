---
title: 'Postupy: Implementace ověření připojení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 245b05d9cfa7ca66dec310bd9a5291def0101d19
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459105"
---
# <a name="how-to-implement-binding-validation"></a>Postupy: Implementace ověření připojení

Tento příklad ukazuje, jak použít <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> a Trigger stylu k poskytnutí vizuální zpětné vazby, která uživatele informují o tom, že je zadána neplatná hodnota, a to na základě vlastního ověřovacího pravidla.

## <a name="example"></a>Příklad

Textový obsah <xref:System.Windows.Controls.TextBox> v následujícím příkladu je vázán na vlastnost `Age` (typu int) objektu zdroje vazby s názvem `ods`. Vazba je nastavená tak, aby používala ověřovací pravidlo s názvem `AgeRangeRule` tak, aby pokud uživatel zadal jiné než číselné znaky nebo hodnotu menší než 21 nebo větší než 130, zobrazí se vedle textového pole červený vykřičník a zobrazí se popis tlačítka s chybovou zprávou, když  uživatel přesune ukazatel myši na textové pole.

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

Následující příklad ukazuje implementaci `AgeRangeRule`, která dědí z <xref:System.Windows.Controls.ValidationRule> a přepisuje metodu <xref:System.Windows.Controls.ValidationRule.Validate%2A>. Pro tuto hodnotu je volána metoda `Int32.Parse`, aby se zajistilo, že neobsahuje žádné neplatné znaky. Metoda <xref:System.Windows.Controls.ValidationRule.Validate%2A> vrátí <xref:System.Windows.Controls.ValidationResult>, která určuje, zda je hodnota platná na základě toho, zda je při analýze zachycena výjimka a zda je hodnota stáří mimo dolní a horní mez.

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

Následující příklad ukazuje vlastní <xref:System.Windows.Controls.ControlTemplate> `validationTemplate`, který vytvoří červený vykřičník pro upozornění uživatele na chybu ověřování. Šablony ovládacích prvků slouží k předefinování vzhledu ovládacího prvku.

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

Jak je znázorněno v následujícím příkladu, <xref:System.Windows.Controls.ToolTip>, která zobrazuje chybovou zprávu, je vytvořena pomocí stylu s názvem `textBoxInError`. Pokud je hodnota <xref:System.Windows.Controls.Validation.HasError%2A> `true`, aktivační událost nastaví popis tlačítka pro aktuální <xref:System.Windows.Controls.TextBox> na první chybu ověření. <xref:System.Windows.Data.Binding.RelativeSource%2A> je nastavena na <xref:System.Windows.Data.RelativeSourceMode.Self>a odkazuje na aktuální prvek.

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

Úplný příklad najdete v tématu [Ukázka ověření vazby](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).
  
Pamatujte, že pokud neposkytnete vlastní <xref:System.Windows.Controls.Validation.ErrorTemplate%2A>, zobrazí se výchozí šablona chyby, která uživateli poskytne vizuální zpětnou vazbu, když dojde k chybě ověření. Další informace najdete v tématu věnovaném ověření dat v [přehledu datových vazeb](../../../desktop-wpf/data/data-binding-overview.md) . [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také poskytuje integrované ověřovací pravidlo, které zachytí výjimky, které jsou vyvolány během aktualizace vlastnosti zdroje vazby. Další informace najdete v tématu <xref:System.Windows.Controls.ExceptionValidationRule>.

## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
