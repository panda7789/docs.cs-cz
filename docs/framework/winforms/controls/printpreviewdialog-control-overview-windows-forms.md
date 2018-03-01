---
title: "PrintPreviewDialog – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 01/08/2018
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1228a3cf39ea412cde341c4c4b8b83e0ab2f0299
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2018
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>Printpreviewdialog – Přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> řízení je předem nakonfigurovaný dialogové okno slouží k zobrazení jak [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) se zobrazí při tisku. Ji použijte v rámci aplikace systému Windows jako simple řešení namísto dialogové okno Vlastní konfigurace. Ovládací prvek obsahuje tlačítka pro tisk, přiblížení, zobrazení jednu nebo více stránek a zavření dialogového okna.  
  
## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody  
 Klíčová vlastnost ovládacího prvku je <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, která nastaví dokument, který chcete zobrazit jejich náhled. Musí být dokument <xref:System.Drawing.Printing.PrintDocument> objektu. Aby bylo možné zobrazit dialogové okno, musí volat jeho <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda. Vyhlazení může zvýšit text zobrazí hladší, ale také může být pomalejší; zobrazení Chcete-li použít, nastavte <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> vlastnost `true`.  
  
 Některé vlastnosti jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl> , <xref:System.Windows.Forms.PrintPreviewDialog> obsahuje. (Není nutné přidejte tuto <xref:System.Windows.Forms.PrintPreviewControl> do formuláře; je automaticky obsažené v <xref:System.Windows.Forms.PrintPreviewDialog> dialogové okno když přidáte do svého formuláře.) Příklady vlastností, které jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl> jsou <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> vlastnosti, které určuje, kolik stránek se zobrazí vodorovně a svisle na ovládací prvek. Dostanete <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> vlastnost jako `PrintPreviewDialog1.PrintPreviewControl.Columns` v [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], `printPreviewDialog1.PrintPreviewControl.Columns` v [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], nebo `printPreviewDialog1->PrintPreviewControl->Columns` v [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].  
  
## <a name="printpreviewdialog-performance"></a>Printpreviewdialog – výkon

Za těchto podmínek <xref:System.Windows.Forms.PrintPreviewDialog> řízení inicializuje velmi pomalu:

- Slouží k síťové tiskárně.
- Jsou uživatelských předvoleb pro tuto tiskárnu, jako je například duplexní nastavení upravit.
  
Pro aplikace běžící v rozhraní .NET Framework 4.5.2, můžete přidat následující klíč \<appSettings > oddílu konfiguračního souboru pro zlepšení výkonu <xref:System.Windows.Forms.PrintPreviewDialog> řízení inicializace:

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
Pokud `EnablePrintPreviewOptimization` klíč je nastaven na jakoukoli jinou hodnotu, nebo pokud klíč neexistuje, není použita optimalizace.

Pro aplikace běžící v rozhraní .NET Framework 4.6 nebo novější verze, můžete přidat následující přepínač tak, aby [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element v [ \<runtime >](../../configure-apps/file-schema/runtime/index.md) části vašeho souboru config aplikace:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
Pokud přepínač není přítomen nebo pokud je nastavena na žádné jiné hodnoty, není použita optimalizace. 

Pokud použijete <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> událostí k úpravě nastavení tiskárny, výkon <xref:System.Windows.Forms.PrintPreviewDialog> řízení nezlepší i v případě, že je nastavena optimalizaci konfigurace přepínače.  

## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [Přehled ovládacího prvku PrintPreviewControl](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [Ovládací prvek PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Ovládací prvky a součásti dialogového okna](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
