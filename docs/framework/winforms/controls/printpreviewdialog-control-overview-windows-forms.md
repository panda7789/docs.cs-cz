---
title: Přehled ovládacího prvku PrintPreviewDialog
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
ms.openlocfilehash: 6fb971493336cda1e04c720dd09147e650918c3a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741406"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>Přehled ovládacího prvku PrintPreviewDialog – (model Windows Forms)

Ovládací prvek model Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> je předem nakonfigurovaný dialog, který slouží k zobrazení toho, jak se bude zobrazovat [PrintDocument](printdocument-component-windows-forms.md) po vytištění. Používejte ho v rámci aplikace pro Windows jako jednoduché řešení namísto konfigurace vlastního dialogového okna. Ovládací prvek obsahuje tlačítka pro tisk, přiblížení, zobrazení jedné nebo více stránek a zavření dialogového okna.

## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody

Vlastnost klíče ovládacího prvku je <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, ve kterém se nastaví náhled dokumentu. Dokument musí být objekt <xref:System.Drawing.Printing.PrintDocument>. Chcete-li zobrazit dialogové okno, je nutné zavolat jeho metodu <xref:System.Windows.Forms.Form.ShowDialog%2A>. Vyhlazení může text zobrazit hladší, ale může také zpomalit zobrazení. Pokud ho chcete použít, nastavte vlastnost <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> na `true`.

Některé vlastnosti jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl>, které obsahuje <xref:System.Windows.Forms.PrintPreviewDialog>. (Tuto <xref:System.Windows.Forms.PrintPreviewControl> nemusíte přidávat do formuláře. je automaticky obsažena v <xref:System.Windows.Forms.PrintPreviewDialog> při přidávání dialogového okna do formuláře). Příklady vlastností, které jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl>, jsou vlastnosti <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>, které určují počet stránek zobrazených vodorovně a svisle na ovládacím prvku. Vlastnost <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> můžete zpřístupnit jako `PrintPreviewDialog1.PrintPreviewControl.Columns` v Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` v vizuálu C#nebo `printPreviewDialog1->PrintPreviewControl->Columns` ve vizuálu. C++

## <a name="printpreviewdialog-performance"></a>PrintPreviewDialog – výkon

V následujících podmínkách se ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog> inicializuje velmi pomalu:

- Použije se síťová tiskárna.
- Uživatelské předvolby pro tuto tiskárnu, například duplexní nastavení, se upraví.

Pro aplikace běžící v .NET Framework 4.5.2 můžete přidat následující klíč do části \<appSettings > konfiguračního souboru, aby se zlepšil výkon při inicializaci ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog>:

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

Pokud je klíč `EnablePrintPreviewOptimization` nastaven na jinou hodnotu, nebo pokud klíč není k dispozici, optimalizace se nepoužije.

Pro aplikace spuštěné v .NET Framework 4,6 nebo novějších verzích můžete do elementu [\<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přidat následující přepínač v sekci [> modulu runtime\<](../../configure-apps/file-schema/runtime/index.md) v konfiguračním souboru aplikace:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

Pokud přepínač není přítomen nebo pokud je nastaven na jinou hodnotu, optimalizace se nepoužije.

Použijete-li událost <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> pro úpravu nastavení tiskárny, výkon ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog> nebude vylepšen ani v případě, že je nastaven přepínač konfigurace optimalizace.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [Přehled ovládacího prvku PrintPreviewControl](printpreviewcontrol-control-overview-windows-forms.md)
- [Ovládací prvek PrintPreviewDialog](printpreviewdialog-control-windows-forms.md)
- [Ovládací prvky a součásti dialogového okna](dialog-box-controls-and-components-windows-forms.md)
