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
ms.openlocfilehash: 32fbdd222e34f642d29255e6c594076b6d2a91e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188835"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="b7fdd-102">Printpreviewdialog – Přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b7fdd-102">PrintPreviewDialog control overview (Windows Forms)</span></span>
<span data-ttu-id="b7fdd-103">Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek je předem nakonfigurované dialogovému oknu slouží k zobrazení jak [PrintDocument](printdocument-component-windows-forms.md) se zobrazí po vytištění.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="b7fdd-104">Použijte v rámci vaší aplikace založené na Windows jako jednoduchým řešením namísto dialogové okno Vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="b7fdd-105">Ovládací prvek obsahuje tlačítka pro tisk, Přiblížit, zobrazení jedné nebo více stránek a zavření dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="b7fdd-106">Klíčové vlastnosti a metody</span><span class="sxs-lookup"><span data-stu-id="b7fdd-106">Key properties and methods</span></span>  
 <span data-ttu-id="b7fdd-107">Klíčová vlastnost ovládacího prvku je <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, který nastaví dokumentu, který má být zobrazen.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="b7fdd-108">Dokument musí být <xref:System.Drawing.Printing.PrintDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="b7fdd-109">Aby bylo možné zobrazit dialogové okno, je nutné volat jeho <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="b7fdd-110">Vyhlazení může zvýšit zobrazí hladší text, ale také může být pomalejší; zobrazení Chcete-li použít, nastavte <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="b7fdd-111">Některé vlastnosti jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl> , který <xref:System.Windows.Forms.PrintPreviewDialog> obsahuje.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="b7fdd-112">(Není potřeba tento <xref:System.Windows.Forms.PrintPreviewControl> pro formuláře; je automaticky obsažené v rámci <xref:System.Windows.Forms.PrintPreviewDialog> po přidání dialogového okna do formuláře.) Příkladem vlastnosti, které jsou k dispozici prostřednictvím <xref:System.Windows.Forms.PrintPreviewControl> jsou <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> vlastnosti, které určují počet stránek zobrazených vodorovně a svisle na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="b7fdd-113">Můžete přistupovat <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> vlastnost jako `PrintPreviewDialog1.PrintPreviewControl.Columns` v jazyce Visual Basic `printPreviewDialog1.PrintPreviewControl.Columns` ve Vizuálu C#, nebo `printPreviewDialog1->PrintPreviewControl->Columns` v [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7fdd-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` in Visual C#, or `printPreviewDialog1->PrintPreviewControl->Columns` in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span></span>  
  
## <a name="printpreviewdialog-performance"></a><span data-ttu-id="b7fdd-114">Printpreviewdialog – výkon</span><span class="sxs-lookup"><span data-stu-id="b7fdd-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="b7fdd-115">Za následujících podmínek <xref:System.Windows.Forms.PrintPreviewDialog> velmi pomalu se inicializuje ovládací prvek:</span><span class="sxs-lookup"><span data-stu-id="b7fdd-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="b7fdd-116">Slouží k síťové tiskárně.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-116">A network printer is used.</span></span>
- <span data-ttu-id="b7fdd-117">Předvolby uživatele pro tuto tiskárnu, jako je například duplexní nastavení, jsou změněny.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-117">User preferences for this printer, such as duplex settings, are modified.</span></span>
  
<span data-ttu-id="b7fdd-118">Pro aplikace běžící na rozhraní .NET Framework 4.5.2, můžete přidat následující klíč \<appSettings > oddílu konfiguračního souboru pro zlepšení výkonu <xref:System.Windows.Forms.PrintPreviewDialog> řídit inicializace:</span><span class="sxs-lookup"><span data-stu-id="b7fdd-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
<span data-ttu-id="b7fdd-119">Pokud `EnablePrintPreviewOptimization` klíč nastavený na jakoukoli jinou hodnotu, nebo pokud není klíč přítomen, optimalizace se nepoužije.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="b7fdd-120">Pro aplikace běžící na rozhraní .NET Framework 4.6 nebo novější verze, můžete přidat následující přepínač tak, aby [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek [ \<runtime >](../../configure-apps/file-schema/runtime/index.md) oddíl konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="b7fdd-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
<span data-ttu-id="b7fdd-121">Pokud není k dispozici přepínač nebo pokud je nastavena na jinou hodnotu, optimalizace se nepoužije.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span> 

<span data-ttu-id="b7fdd-122">Pokud používáte <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> událostí k úpravě nastavení tiskárny, výkon <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek nezlepší i v případě, že je nastavena k přepnutí optimalizace konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b7fdd-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>  

## <a name="see-also"></a><span data-ttu-id="b7fdd-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7fdd-123">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [<span data-ttu-id="b7fdd-124">Přehled ovládacího prvku PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="b7fdd-124">PrintPreviewControl Control Overview</span></span>](printpreviewcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="b7fdd-125">Ovládací prvek PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="b7fdd-125">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="b7fdd-126">Ovládací prvky a součásti dialogového okna</span><span class="sxs-lookup"><span data-stu-id="b7fdd-126">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
