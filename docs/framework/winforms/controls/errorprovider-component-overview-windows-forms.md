---
title: Přehled komponenty ErrorProvider
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: b66e97d97d0d8c2ea4e9bdba29f8ff35e486e1f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745790"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider – přehled komponenty (Windows Forms)
Komponenta model Windows Forms [ErrorProvider](errorprovider-component-windows-forms.md) slouží k ověření vstupu uživatele na formuláři nebo ovládacím prvku. Obvykle se používá ve spojení s ověřováním vstupu uživatele na formuláři nebo při zobrazení chyb v rámci datové sady. Poskytovatel chyb je lepší alternativou než zobrazení chybové zprávy v okně se zprávou, protože když se okno se zprávou zavře, chybová zpráva už není zobrazená. Komponenta <xref:System.Windows.Forms.ErrorProvider> zobrazuje ikonu chyby (![bílého vykřičníku uvnitř červeného kruhu.](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)) vedle příslušného ovládacího prvku, jako je například textové pole; Když uživatel umístí ukazatel myši nad ikonu chyby, zobrazí se popis, který zobrazuje řetězec chybové zprávy.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 <xref:System.Windows.Forms.ErrorProvider> vlastností klíče komponenty jsou <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>a <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Při použití součásti <xref:System.Windows.Forms.ErrorProvider> s ovládacími prvky vázanými na data musí být vlastnost <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> nastavena na příslušný kontejner (obvykle formulář Windows), aby mohla komponenta zobrazit ve formuláři ikonu chyby. Při přidání komponenty v návrháři je vlastnost <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> nastavena na obsahující formulář; Přidáte-li ovládací prvek do kódu, je nutné jej nastavit sami.  
  
 Vlastnost <xref:System.Windows.Forms.ErrorProvider.Icon%2A> lze nastavit na vlastní ikonu chyby namísto výchozího. Pokud je nastavena vlastnost <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, komponenta <xref:System.Windows.Forms.ErrorProvider> může zobrazit chybové zprávy pro datovou sadu. Klíčovou metodou součásti <xref:System.Windows.Forms.ErrorProvider> je <xref:System.Windows.Forms.ErrorProvider.SetError%2A> metoda, která určuje řetězec chybové zprávy a kde by se měla zobrazit ikona chyby.  
  
> [!NOTE]
> Součást <xref:System.Windows.Forms.ErrorProvider> neposkytuje integrovanou podporu pro klienty přístupnosti. Aby byla aplikace přístupná při použití této součásti, je nutné poskytnout další, přístupný mechanismus zpětné vazby.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ErrorProvider>
- [Postupy: Zobrazování chyb v prvku DataSet pomocí komponenty Windows Forms ErrorProvider](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Postupy: Zobrazení ikon chyb pro ověřování formuláře pomocí komponenty Windows Forms ErrorProvider](display-error-icons-for-form-validation-with-wf-errorprovider.md)
