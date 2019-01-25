---
title: PrintPreviewDialog – přehled ovládacího prvku (Windows Forms)
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e28a6c82a8dd40885c04c56f2adfb3d38e674066
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667554"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>Printpreviewdialog – Přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek je předem nakonfigurované dialogovému oknu slouží k zobrazení jak [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) se zobrazí po vytištění. Použijte v rámci vaší aplikace založené na Windows jako jednoduchým řešením namísto dialogové okno Vlastní konfigurace. Ovládací prvek obsahuje tlačítka pro tisk, Přiblížit, zobrazení jedné nebo více stránek a zavření dialogového okna.  
  
## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody  
 Klíčová vlastnost ovládacího prvku je <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, který nastaví dokumentu, který má být zobrazen. Dokument musí být <xref:System.Drawing.Printing.PrintDocument> objektu. Aby bylo možné zobrazit dialogové okno, je nutné volat jeho <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda. Vyhlazení může zvýšit zobrazí hladší text, ale také může být pomalejší; zobrazení Chcete-li použít, nastavte <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> vlastnost `true`.  
  
 Některé vlastnosti jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl> , který <xref:System.Windows.Forms.PrintPreviewDialog> obsahuje. (Není potřeba tento <xref:System.Windows.Forms.PrintPreviewControl> pro formuláře; je automaticky obsažené v rámci <xref:System.Windows.Forms.PrintPreviewDialog> po přidání dialogového okna do formuláře.) Příkladem vlastnosti, které jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl> jsou <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> vlastnosti, které určují počet stránek zobrazených vodorovně a svisle na ovládacím prvku. Můžete přistupovat <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> vlastnost jako `PrintPreviewDialog1.PrintPreviewControl.Columns` v jazyce Visual Basic `printPreviewDialog1.PrintPreviewControl.Columns` ve Vizuálu C#, nebo `printPreviewDialog1->PrintPreviewControl->Columns` v [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].  
  
## <a name="printpreviewdialog-performance"></a>Printpreviewdialog – výkon

Za následujících podmínek <xref:System.Windows.Forms.PrintPreviewDialog> velmi pomalu se inicializuje ovládací prvek:

- Slouží k síťové tiskárně.
- Předvolby uživatele pro tuto tiskárnu, jako je například duplexní nastavení, jsou změněny.
  
Pro aplikace běžící na rozhraní .NET Framework 4.5.2, můžete přidat následující klíč \<appSettings > oddílu konfiguračního souboru pro zlepšení výkonu <xref:System.Windows.Forms.PrintPreviewDialog> řídit inicializace:

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
Pokud `EnablePrintPreviewOptimization` klíč nastavený na jakoukoli jinou hodnotu, nebo pokud není klíč přítomen, optimalizace se nepoužije.

Pro aplikace běžící na rozhraní .NET Framework 4.6 nebo novější verze, můžete přidat následující přepínač tak, aby [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek [ \<runtime >](../../configure-apps/file-schema/runtime/index.md) oddíl konfiguračního souboru aplikace:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
Pokud není k dispozici přepínač nebo pokud je nastavena na jinou hodnotu, optimalizace se nepoužije. 

Pokud používáte <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> událostí k úpravě nastavení tiskárny, výkon <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek nezlepší i v případě, že je nastavena k přepnutí optimalizace konfigurace.  

## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.PrintPreviewDialog>
- [Přehled ovládacího prvku PrintPreviewControl](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)
- [Ovládací prvek PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)
- [Ovládací prvky a součásti dialogového okna](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
