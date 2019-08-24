---
title: 'Postupy: Přidávání ovládacích prvků ActiveX do Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 8c4c6c3f96c49401b032e360314794cc800c0551
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987060"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="147dc-102">Postupy: Přidávání ovládacích prvků ActiveX do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="147dc-102">How to: Add ActiveX Controls to Windows Forms</span></span>

<span data-ttu-id="147dc-103">I když je Návrhář formulářů v aplikaci Visual Studio optimalizováno pro hostování model Windows Formsch ovládacích prvků, můžete také umístit ovládací prvky ActiveX na model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="147dc-103">While the Windows Forms Designer in Visual Studio is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>

> [!CAUTION]
> <span data-ttu-id="147dc-104">Existují omezení výkonu pro model Windows Forms, když jsou do nich přidány ovládací prvky ActiveX.</span><span class="sxs-lookup"><span data-stu-id="147dc-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>

<span data-ttu-id="147dc-105">Než přidáte ovládací prvky ActiveX do formuláře, je nutné je přidat do panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="147dc-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="147dc-106">Další informace naleznete v tématu [komponenty modelu COM, dialogové okno přizpůsobení sady nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="147dc-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span></span>

## <a name="add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="147dc-107">Přidání ovládacího prvku ActiveX do formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="147dc-107">Add an ActiveX control to your Windows Form</span></span>

<span data-ttu-id="147dc-108">Chcete-li přidat ovládací prvek ActiveX do formuláře Windows, dvakrát klikněte na ovládací prvek na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="147dc-108">To add an ActiveX control to your Windows Form, double-click the control on the Toolbox.</span></span>

<span data-ttu-id="147dc-109">Visual Studio přidá všechny odkazy na ovládací prvek v projektu.</span><span class="sxs-lookup"><span data-stu-id="147dc-109">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="147dc-110">Další informace o akcích, které je potřeba vzít v úvahu při používání ovládacích prvků ActiveX na model Windows Forms, najdete v tématu [aspekty hostování ovládacího prvku ActiveX ve formuláři Windows](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="147dc-110">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>

> [!NOTE]
> <span data-ttu-id="147dc-111">Nástroj pro import ovládacího prvku ActiveX (AxImp. exe) vytvoří argumenty události jiného typu, než model Windows Forms se čekalo při dovozu dynamických knihoven ActiveX.</span><span class="sxs-lookup"><span data-stu-id="147dc-111">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="147dc-112">Argumenty vytvořené pomocí AxImp. exe jsou podobné následujícímu: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, když `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="147dc-112">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="147dc-113">Mějte na paměti, že tato nepravidelnost nebrání v normálním fungování kódu.</span><span class="sxs-lookup"><span data-stu-id="147dc-113">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="147dc-114">Podrobnosti najdete v tématu [model Windows Forms Importéru ovládacího prvku ActiveX (Aximp. exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="147dc-114">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="147dc-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="147dc-115">See also</span></span>

- [<span data-ttu-id="147dc-116">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="147dc-116">Windows Forms Controls</span></span>](index.md)
- <span data-ttu-id="147dc-117">[Ovládací prvky a programovatelné objekty v porovnání s různými jazyky a knihovnami](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="147dc-117">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="147dc-118">Postupy: Přidat ovládací prvky do model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="147dc-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="147dc-119">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="147dc-119">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="147dc-120">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="147dc-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="147dc-121">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="147dc-121">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
