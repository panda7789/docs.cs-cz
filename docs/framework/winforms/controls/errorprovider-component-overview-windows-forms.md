---
title: ErrorProvider – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: 485e7a17073d72618b9599113179cddde748e697
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972017"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider – přehled komponenty (Windows Forms)
Windows Forms [ErrorProvider](errorprovider-component-windows-forms.md) komponenty se používá k ověření vstupu uživatele na formulář nebo ovládací prvek. To se obvykle používá ve spojení s ověřování uživatelského vstupu ve formuláři nebo zobrazování chyb v prvku dataset. Poskytovatele chyba je lepší alternativou než zobrazení chybové zprávy v okně se zprávou, protože když se zavře okno se zprávou, chybová zpráva již není viditelný. <xref:System.Windows.Forms.ErrorProvider> Komponenty zobrazuje ikonu chyby (![ErrorProvider ikonu](./media/vberrorprovidericon.gif "vbErrorProviderIcon")) vedle příslušné ovládacího prvku, jako je textové pole, když uživatel přemístí ukazatel myši ikona chyby, popisek se zobrazí, zobrazuje řetězec chybové zprávy.  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 <xref:System.Windows.Forms.ErrorProvider> Klíčové vlastnosti komponenty jsou <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, a <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Při použití <xref:System.Windows.Forms.ErrorProvider> komponentu pomocí ovládacích prvků vázaných na data, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> musí být nastavena vlastnost do odpovídajícího kontejneru (zpravidla formulář Windows) v pořadí pro součást se zobrazí ikona chyby na formuláři. Když se přidá komponentu v návrháři <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> je nastavena na nadřazený formulář; Pokud přidáte ovládací prvek v kódu, musíte jej nastavit sami.  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A> Vlastnost lze nastavit ikonu Vlastní chybové místo výchozího. Když <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> je vlastnost nastavena, <xref:System.Windows.Forms.ErrorProvider> součásti můžete zobrazit chybové zprávy pro datovou sadu. Metodu klíče <xref:System.Windows.Forms.ErrorProvider> komponenta je <xref:System.Windows.Forms.ErrorProvider.SetError%2A> metoda, která určuje řetězec chybové zprávy a kde by se měla zobrazit ikona chyby.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ErrorProvider> Součást neposkytuje integrovanou podporu pro klienty usnadnění. Pokud chcete zpřístupnit svoji aplikaci při použití této součásti, je nutné zadat mechanismus zpětné vazby další, přístupné.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ErrorProvider>
- [Postupy: Zobrazování chyb v prvku DataSet pomocí komponenty Windows Forms ErrorProvider](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Postupy: Zobrazení ikon chyb pro ověřování formuláře pomocí součásti Windows Forms ErrorProvider](display-error-icons-for-form-validation-with-wf-errorprovider.md)
