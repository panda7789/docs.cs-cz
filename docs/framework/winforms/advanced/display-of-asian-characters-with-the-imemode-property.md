---
title: Zobrazení asijských znaků s vlastností ImeMode
ms.date: 03/30/2017
helpviewer_keywords:
- Asian languages [Windows Forms], displaying with ImeMode
- Chinese characters [Windows Forms], displaying with ImeMode
- IME mode
- Japanese characters [Windows Forms], displaying with ImeMode
- international applications [Windows Forms], character display
- international characters
- Korean characters
- Asian languages
- Input Method Editor (IME), mode
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
ms.openlocfilehash: 25602e1a878443bd54411dfd6481581abebda5c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500516"
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a><span data-ttu-id="16108-102">Zobrazení asijských znaků s vlastností ImeMode</span><span class="sxs-lookup"><span data-stu-id="16108-102">Display of Asian Characters with the ImeMode Property</span></span>
<span data-ttu-id="16108-103"><xref:System.Windows.Forms.Control.ImeMode%2A> Vlastnost používá formuláře a ovládací prvky vynutit konkrétní režim pro editor IME (IME).</span><span class="sxs-lookup"><span data-stu-id="16108-103">The <xref:System.Windows.Forms.Control.ImeMode%2A> property is used by forms and controls to force a specific mode for an input method editor (IME).</span></span> <span data-ttu-id="16108-104">Editor IME je nezbytné součásti pro psaní skriptů čínštiny, japonštiny a korejštiny, protože tyto systémy zápisu mít více znaků, než může být zakódován regulární klávesnice.</span><span class="sxs-lookup"><span data-stu-id="16108-104">The IME is an essential component for writing Chinese, Japanese, and Korean scripts, since these writing systems have more characters than can be encoded for a regular keyboard.</span></span> <span data-ttu-id="16108-105">Chcete například povolit pouze znaky ASCII v konkrétní textové pole.</span><span class="sxs-lookup"><span data-stu-id="16108-105">For example, you may want to allow only ASCII characters in a particular text box.</span></span> <span data-ttu-id="16108-106">V takovém případě můžete nastavit <xref:System.Windows.Forms.Control.ImeMode%2A> vlastnost <xref:System.Windows.Forms.ImeMode> a uživatelé budou moct jenom pro tento konkrétní textového pole zadejte znaky ASCII.</span><span class="sxs-lookup"><span data-stu-id="16108-106">In such a case you can set the <xref:System.Windows.Forms.Control.ImeMode%2A> property to <xref:System.Windows.Forms.ImeMode> and users will only be able to enter ASCII characters for that particular text box.</span></span> <span data-ttu-id="16108-107">Výchozí hodnota <xref:System.Windows.Forms.Control.ImeMode%2A> vlastnost <xref:System.Windows.Forms.ImeMode>, takže pokud jste nastavili vlastnost formuláře, všechny ovládací prvky ve formuláři zdědí toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="16108-107">The default value of the <xref:System.Windows.Forms.Control.ImeMode%2A> property is <xref:System.Windows.Forms.ImeMode>, so if you set the property for a form, all controls on the form will inherit that setting.</span></span> <span data-ttu-id="16108-108">Další informace najdete v tématu <xref:System.Windows.Forms.Control.ImeMode%2A> ) a <xref:System.Windows.Forms.ImeMode>.</span><span class="sxs-lookup"><span data-stu-id="16108-108">For more information, see <xref:System.Windows.Forms.Control.ImeMode%2A> ) and <xref:System.Windows.Forms.ImeMode>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16108-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16108-109">See also</span></span>

- [<span data-ttu-id="16108-110">Globalizace aplikací Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16108-110">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
