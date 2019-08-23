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
ms.openlocfilehash: 3cfd3f306d4a18ce8a194b5197060fbca1d157d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965284"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider – přehled komponenty (Windows Forms)
Komponenta model Windows Forms [ErrorProvider](errorprovider-component-windows-forms.md) slouží k ověření vstupu uživatele na formuláři nebo ovládacím prvku. Obvykle se používá ve spojení s ověřováním vstupu uživatele na formuláři nebo při zobrazení chyb v rámci datové sady. Poskytovatel chyb je lepší alternativou než zobrazení chybové zprávy v okně se zprávou, protože když se okno se zprávou zavře, chybová zpráva už není zobrazená. Tato <xref:System.Windows.Forms.ErrorProvider> součást zobrazuje ikonu chyby (![bílý vykřičník uvnitř červeného kruhu.](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)) vedle příslušného ovládacího prvku, jako je například textové pole; když uživatel umístí ukazatel myši nad ikonu chyby, zobrazí se popis. Zobrazuje se řetězec chybové zprávy.  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 Klíčové vlastnosti <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>komponentyjsou, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>a. <xref:System.Windows.Forms.ErrorProvider.Icon%2A> <xref:System.Windows.Forms.ErrorProvider> Při použití <xref:System.Windows.Forms.ErrorProvider> komponenty s ovládacími prvky <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> vázanými na data musí být vlastnost nastavena na příslušný kontejner (obvykle formulář Windows), aby součást zobrazovala ikonu chyby ve formuláři. Při přidání komponenty v Návrháři <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> je vlastnost nastavena na obsahující formulář; Pokud ovládací prvek přidáte v kódu, je nutné jej nastavit sami.  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A> Vlastnost lze nastavit na vlastní ikonu chyby namísto výchozího. Když je nastavena <xref:System.Windows.Forms.ErrorProvider>vlastnost, komponenta může zobrazit chybové zprávy pro datovou sadu. <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> Klíčovou metodou <xref:System.Windows.Forms.ErrorProvider> komponenty <xref:System.Windows.Forms.ErrorProvider.SetError%2A> je metoda, která určuje řetězec chybové zprávy a kde se má zobrazit ikona chyby.  
  
> [!NOTE]
> Tato <xref:System.Windows.Forms.ErrorProvider> součást neposkytuje integrovanou podporu pro klienty přístupnosti. Aby byla aplikace přístupná při použití této součásti, je nutné poskytnout další, přístupný mechanismus zpětné vazby.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ErrorProvider>
- [Postupy: Zobrazení chyb v rámci datové sady pomocí komponenty model Windows Forms ErrorProvider](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Postupy: Zobrazit chybové ikony pro ověření formuláře pomocí součásti model Windows Forms ErrorProvider](display-error-icons-for-form-validation-with-wf-errorprovider.md)
