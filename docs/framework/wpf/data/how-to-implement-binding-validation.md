---
title: 'Postupy: Implementace ověření připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 347e38ba036e5c1a716a9edb75572c1a49f99631
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556962"
---
# <a name="how-to-implement-binding-validation"></a>Postupy: Implementace ověření připojení
Tento příklad ukazuje, jak používat <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> a aktivační události styl visual svůj názor informovat uživatele, pokud je zadaná neplatná hodnota, podle vlastního ověřovacího pravidla.  
  
## <a name="example"></a>Příklad  
 Obsah textu <xref:System.Windows.Controls.TextBox> v následujícím příkladu je vázána `Age` vlastnost (typ int) s názvem zdrojového objektu vazby `ods`. Vazba je nastavit tak, aby použijte ověřovací pravidlo s názvem `AgeRangeRule` tak, aby pokud uživatel zadá jiné než číselné znaky nebo hodnotu, která je menší než 21 nebo větší než 130, textovém poli se zobrazí červený vykřičník a popis tlačítka s chybovou zprávou kde n uživatel přesune ukazatel myši nad textové pole.  
  
 [!code-xaml[BindValidation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 Následující příklad ukazuje implementaci `AgeRangeRule`, který dědí z <xref:System.Windows.Controls.ValidationRule> a přepíše <xref:System.Windows.Controls.ValidationRule.Validate%2A> metoda. Int32.Parse() metoda je volána na hodnotu a ujistěte se, zda neobsahuje žádné neplatné znaky. <xref:System.Windows.Controls.ValidationRule.Validate%2A> Metoda vrátí <xref:System.Windows.Controls.ValidationResult> určující, pokud hodnota je platná založené na tom, jestli je výjimka zachycena při analýze a jestli je hodnota stáří mimo dolní a horní meze.  
  
 [!code-csharp[BindValidation#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 Následující příklad ukazuje vlastní <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` vytvářející červený vykřičník a upozorní uživatele k chybě ověření. Ovládací prvek šablon se používají k znovu definovat vzhledu ovládacího prvku.  
  
 [!code-xaml[BindValidation#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 Jak je znázorněno v následujícím příkladu <xref:System.Windows.Controls.ToolTip> , zobrazí se chybová zpráva vytvořena pomocí styl s názvem `textBoxInError`. Pokud hodnota <xref:System.Windows.Controls.Validation.HasError%2A> je `true`, aktivační událost nastaví popisek přesunutí aktuálního <xref:System.Windows.Controls.TextBox> do své první chyby ověření. <xref:System.Windows.Data.Binding.RelativeSource%2A> Je nastaven na <xref:System.Windows.Data.RelativeSourceMode.Self>odkazující na aktuálního elementu.  
  
 [!code-xaml[BindValidation#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 Úplný příklad najdete v tématu [vazby Ukázka ověřování](http://go.microsoft.com/fwlink/?LinkID=159972).  
  
 Všimněte si, že pokud nezadáte vlastní <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> výchozí šablony chyba se zobrazí k poskytnutí zpětné vazby visual pro uživatele, když dojde k chybě ověření. V části "Ověření dat" v [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md) Další informace. Navíc [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje integrované ověřovací pravidlo, které zachytí výjimky, které jsou vyvolány během aktualizace zdrojová vlastnost vazby. Další informace naleznete v tématu <xref:System.Windows.Controls.ExceptionValidationRule>.  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
