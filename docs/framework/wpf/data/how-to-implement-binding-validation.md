---
title: 'Postupy: Implementace ověření připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 5e91ab9fbd2fdeb0aa5d836a1eedfb5e0b45ecba
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510449"
---
# <a name="how-to-implement-binding-validation"></a>Postupy: Implementace ověření připojení
Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> a aktivační událost stylu poskytnout vizuální zpětnou vazbu a informuje uživatele, pokud je zadána neplatná hodnota, podle vlastního ověřovacího pravidla.  
  
## <a name="example"></a>Příklad  
 Obsah textu <xref:System.Windows.Controls.TextBox> v následujícím příkladu je vázán na `Age` vlastnosti (typ int) objektu vazby zdroje s názvem `ods`. Vazba byla nastavená pro použití ověřovacího pravidla s názvem `AgeRangeRule` tak, že pokud uživatel zadá jiné než číselné znaky nebo hodnotu, která je menší než 21 nebo větší než 130, vedle textového pole se zobrazí červený vykřičník a popisku tlačítka s chybovou zprávou kde n uživatel pohybuje ukazatelem myši přes textové pole.  
  
 [!code-xaml[BindValidation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 Následující příklad ukazuje implementaci `AgeRangeRule`, který dědí z <xref:System.Windows.Controls.ValidationRule> a přepíše <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody. Je volána metoda Int32.Parse() na hodnotu a ujistěte se, zda neobsahuje neplatné znaky. <xref:System.Windows.Controls.ValidationRule.Validate%2A> Metoda vrátí hodnotu <xref:System.Windows.Controls.ValidationResult> , který označuje, zda je hodnota platná na základě Určuje, zda je zachycena výjimka při analýze a určuje, zda je hodnota stáří mimo dolní a horní hranice.  
  
 [!code-csharp[BindValidation#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 Následující příklad ukazuje vlastní <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` , který vytváří červený vykřičník a upozorňovaly uživatele k chybě ověřování. Šablony ovládacích prvků se používají k předefinování vzhledu ovládacího prvku.  
  
 [!code-xaml[BindValidation#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 Jak je znázorněno v následujícím příkladu <xref:System.Windows.Controls.ToolTip> , který se zobrazí chybová zpráva je vytvořený pomocí style s názvem `textBoxInError`. Pokud hodnota <xref:System.Windows.Controls.Validation.HasError%2A> je `true`, aktivační událost nastaví popis tlačítka aktuálního <xref:System.Windows.Controls.TextBox> do své první chyby ověření. <xref:System.Windows.Data.Binding.RelativeSource%2A> Je nastavena na <xref:System.Windows.Data.RelativeSourceMode.Self>odkazující na aktuální prvek.  
  
 [!code-xaml[BindValidation#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 Kompletní příklad naleznete v tématu [vazby Ukázka ověřování](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
 Všimněte si, že pokud nezadáte vlastní <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> výchozí šablonu chyb se zobrazí na poskytují uživateli vizuální zpětnou vazbu, když dojde k chybě ověřování. Naleznete v části "Ověření dat" v [přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md) Další informace. Navíc [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje integrované ověřovací pravidlo, které zachytí výjimky, které jsou vyvolány při aktualizaci vlastnosti zdroje vazby. Další informace naleznete v tématu <xref:System.Windows.Controls.ExceptionValidationRule>.  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
