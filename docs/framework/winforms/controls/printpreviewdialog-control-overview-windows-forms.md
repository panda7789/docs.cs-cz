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
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="8ec2f-102">Přehled ovládacího prvku PrintPreviewDialog – (model Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="8ec2f-102">PrintPreviewDialog control overview (Windows Forms)</span></span>

<span data-ttu-id="8ec2f-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> je předem nakonfigurovaný dialog, který slouží k zobrazení toho, jak se bude zobrazovat [PrintDocument](printdocument-component-windows-forms.md) po vytištění.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="8ec2f-104">Používejte ho v rámci aplikace pro Windows jako jednoduché řešení namísto konfigurace vlastního dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="8ec2f-105">Ovládací prvek obsahuje tlačítka pro tisk, přiblížení, zobrazení jedné nebo více stránek a zavření dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="8ec2f-106">Klíčové vlastnosti a metody</span><span class="sxs-lookup"><span data-stu-id="8ec2f-106">Key properties and methods</span></span>

<span data-ttu-id="8ec2f-107">Vlastnost klíče ovládacího prvku je <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, ve kterém se nastaví náhled dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="8ec2f-108">Dokument musí být objekt <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="8ec2f-109">Chcete-li zobrazit dialogové okno, je nutné zavolat jeho metodu <xref:System.Windows.Forms.Form.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="8ec2f-110">Vyhlazení může text zobrazit hladší, ale může také zpomalit zobrazení. Pokud ho chcete použít, nastavte vlastnost <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>

<span data-ttu-id="8ec2f-111">Některé vlastnosti jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl>, které obsahuje <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="8ec2f-112">(Tuto <xref:System.Windows.Forms.PrintPreviewControl> nemusíte přidávat do formuláře. je automaticky obsažena v <xref:System.Windows.Forms.PrintPreviewDialog> při přidávání dialogového okna do formuláře). Příklady vlastností, které jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl>, jsou vlastnosti <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>, které určují počet stránek zobrazených vodorovně a svisle na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="8ec2f-113">Vlastnost <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> můžete zpřístupnit jako `PrintPreviewDialog1.PrintPreviewControl.Columns` v Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` v vizuálu C#nebo `printPreviewDialog1->PrintPreviewControl->Columns` ve vizuálu. C++</span><span class="sxs-lookup"><span data-stu-id="8ec2f-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` in Visual C#, or `printPreviewDialog1->PrintPreviewControl->Columns` in Visual C++.</span></span>

## <a name="printpreviewdialog-performance"></a><span data-ttu-id="8ec2f-114">PrintPreviewDialog – výkon</span><span class="sxs-lookup"><span data-stu-id="8ec2f-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="8ec2f-115">V následujících podmínkách se ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog> inicializuje velmi pomalu:</span><span class="sxs-lookup"><span data-stu-id="8ec2f-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="8ec2f-116">Použije se síťová tiskárna.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-116">A network printer is used.</span></span>
- <span data-ttu-id="8ec2f-117">Uživatelské předvolby pro tuto tiskárnu, například duplexní nastavení, se upraví.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-117">User preferences for this printer, such as duplex settings, are modified.</span></span>

<span data-ttu-id="8ec2f-118">Pro aplikace běžící v .NET Framework 4.5.2 můžete přidat následující klíč do části \<appSettings > konfiguračního souboru, aby se zlepšil výkon při inicializaci ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog>:</span><span class="sxs-lookup"><span data-stu-id="8ec2f-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

<span data-ttu-id="8ec2f-119">Pokud je klíč `EnablePrintPreviewOptimization` nastaven na jinou hodnotu, nebo pokud klíč není k dispozici, optimalizace se nepoužije.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="8ec2f-120">Pro aplikace spuštěné v .NET Framework 4,6 nebo novějších verzích můžete do elementu [\<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přidat následující přepínač v sekci [> modulu runtime\<](../../configure-apps/file-schema/runtime/index.md) v konfiguračním souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="8ec2f-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

<span data-ttu-id="8ec2f-121">Pokud přepínač není přítomen nebo pokud je nastaven na jinou hodnotu, optimalizace se nepoužije.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span>

<span data-ttu-id="8ec2f-122">Použijete-li událost <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> pro úpravu nastavení tiskárny, výkon ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog> nebude vylepšen ani v případě, že je nastaven přepínač konfigurace optimalizace.</span><span class="sxs-lookup"><span data-stu-id="8ec2f-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ec2f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ec2f-123">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [<span data-ttu-id="8ec2f-124">Přehled ovládacího prvku PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="8ec2f-124">PrintPreviewControl Control Overview</span></span>](printpreviewcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="8ec2f-125">Ovládací prvek PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="8ec2f-125">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="8ec2f-126">Ovládací prvky a součásti dialogového okna</span><span class="sxs-lookup"><span data-stu-id="8ec2f-126">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
