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
ms.openlocfilehash: 0946220017fb78775f045bb225d84ea95aecd06b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538334"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="ce88f-102">Printpreviewdialog – Přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ce88f-102">PrintPreviewDialog control overview (Windows Forms)</span></span>
<span data-ttu-id="ce88f-103">Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> řízení je předem nakonfigurovaný dialogové okno slouží k zobrazení jak [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) se zobrazí při tisku.</span><span class="sxs-lookup"><span data-stu-id="ce88f-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="ce88f-104">Ji použijte v rámci aplikace systému Windows jako simple řešení namísto dialogové okno Vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="ce88f-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="ce88f-105">Ovládací prvek obsahuje tlačítka pro tisk, přiblížení, zobrazení jednu nebo více stránek a zavření dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="ce88f-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="ce88f-106">Klíčové vlastnosti a metody</span><span class="sxs-lookup"><span data-stu-id="ce88f-106">Key properties and methods</span></span>  
 <span data-ttu-id="ce88f-107">Klíčová vlastnost ovládacího prvku je <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, která nastaví dokument, který chcete zobrazit jejich náhled.</span><span class="sxs-lookup"><span data-stu-id="ce88f-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="ce88f-108">Musí být dokument <xref:System.Drawing.Printing.PrintDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="ce88f-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="ce88f-109">Aby bylo možné zobrazit dialogové okno, musí volat jeho <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ce88f-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="ce88f-110">Vyhlazení může zvýšit text zobrazí hladší, ale také může být pomalejší; zobrazení Chcete-li použít, nastavte <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="ce88f-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="ce88f-111">Některé vlastnosti jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl> , <xref:System.Windows.Forms.PrintPreviewDialog> obsahuje.</span><span class="sxs-lookup"><span data-stu-id="ce88f-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="ce88f-112">(Není nutné přidejte tuto <xref:System.Windows.Forms.PrintPreviewControl> do formuláře; je automaticky obsažené v <xref:System.Windows.Forms.PrintPreviewDialog> dialogové okno když přidáte do svého formuláře.) Příklady vlastností, které jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl> jsou <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> vlastnosti, které určuje, kolik stránek se zobrazí vodorovně a svisle na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ce88f-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="ce88f-113">Dostanete <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> vlastnost jako `PrintPreviewDialog1.PrintPreviewControl.Columns` v jazyce Visual Basic `printPreviewDialog1.PrintPreviewControl.Columns` v jazyce Visual C# nebo `printPreviewDialog1->PrintPreviewControl->Columns` v [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ce88f-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` in Visual C#, or `printPreviewDialog1->PrintPreviewControl->Columns` in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span></span>  
  
## <a name="printpreviewdialog-performance"></a><span data-ttu-id="ce88f-114">Printpreviewdialog – výkon</span><span class="sxs-lookup"><span data-stu-id="ce88f-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="ce88f-115">Za těchto podmínek <xref:System.Windows.Forms.PrintPreviewDialog> řízení inicializuje velmi pomalu:</span><span class="sxs-lookup"><span data-stu-id="ce88f-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="ce88f-116">Slouží k síťové tiskárně.</span><span class="sxs-lookup"><span data-stu-id="ce88f-116">A network printer is used.</span></span>
- <span data-ttu-id="ce88f-117">Jsou uživatelských předvoleb pro tuto tiskárnu, jako je například duplexní nastavení upravit.</span><span class="sxs-lookup"><span data-stu-id="ce88f-117">User preferences for this printer, such as duplex settings, are modified.</span></span>
  
<span data-ttu-id="ce88f-118">Pro aplikace běžící v rozhraní .NET Framework 4.5.2, můžete přidat následující klíč \<appSettings > oddílu konfiguračního souboru pro zlepšení výkonu <xref:System.Windows.Forms.PrintPreviewDialog> řízení inicializace:</span><span class="sxs-lookup"><span data-stu-id="ce88f-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
<span data-ttu-id="ce88f-119">Pokud `EnablePrintPreviewOptimization` klíč je nastaven na jakoukoli jinou hodnotu, nebo pokud klíč neexistuje, není použita optimalizace.</span><span class="sxs-lookup"><span data-stu-id="ce88f-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="ce88f-120">Pro aplikace běžící v rozhraní .NET Framework 4.6 nebo novější verze, můžete přidat následující přepínač tak, aby [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element v [ \<runtime >](../../configure-apps/file-schema/runtime/index.md) části vašeho souboru config aplikace:</span><span class="sxs-lookup"><span data-stu-id="ce88f-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
<span data-ttu-id="ce88f-121">Pokud přepínač není přítomen nebo pokud je nastavena na žádné jiné hodnoty, není použita optimalizace.</span><span class="sxs-lookup"><span data-stu-id="ce88f-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span> 

<span data-ttu-id="ce88f-122">Pokud použijete <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> událostí k úpravě nastavení tiskárny, výkon <xref:System.Windows.Forms.PrintPreviewDialog> řízení nezlepší i v případě, že je nastavena optimalizaci konfigurace přepínače.</span><span class="sxs-lookup"><span data-stu-id="ce88f-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>  

## <a name="see-also"></a><span data-ttu-id="ce88f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce88f-123">See also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [<span data-ttu-id="ce88f-124">Přehled ovládacího prvku PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="ce88f-124">PrintPreviewControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="ce88f-125">Ovládací prvek PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="ce88f-125">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="ce88f-126">Ovládací prvky a součásti dialogového okna</span><span class="sxs-lookup"><span data-stu-id="ce88f-126">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
