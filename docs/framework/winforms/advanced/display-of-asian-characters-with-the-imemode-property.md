---
title: "Zobrazení asijských znaků s vlastností ImeMode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ba86b0c1343d84e65f0e3f9ff48a09b3a80a27a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a><span data-ttu-id="cddb2-102">Zobrazení asijských znaků s vlastností ImeMode</span><span class="sxs-lookup"><span data-stu-id="cddb2-102">Display of Asian Characters with the ImeMode Property</span></span>
<span data-ttu-id="cddb2-103"><xref:System.Windows.Forms.Control.ImeMode%2A> Vlastnost je používána formuláře a ovládací prvky můžete vynutit konkrétní režim pro editor IME (IME).</span><span class="sxs-lookup"><span data-stu-id="cddb2-103">The <xref:System.Windows.Forms.Control.ImeMode%2A> property is used by forms and controls to force a specific mode for an input method editor (IME).</span></span> <span data-ttu-id="cddb2-104">Editor IME je základní součástí pro psaní skriptů čínština, japonština nebo korejština, protože tyto systémy zápisu obsahují více znaků, než může být zakódován pro běžnou klávesnici.</span><span class="sxs-lookup"><span data-stu-id="cddb2-104">The IME is an essential component for writing Chinese, Japanese, and Korean scripts, since these writing systems have more characters than can be encoded for a regular keyboard.</span></span> <span data-ttu-id="cddb2-105">Chcete třeba povolit jenom znaky ASCII v konkrétní textové pole.</span><span class="sxs-lookup"><span data-stu-id="cddb2-105">For example, you may want to allow only ASCII characters in a particular text box.</span></span> <span data-ttu-id="cddb2-106">V takovém případě můžete nastavit <xref:System.Windows.Forms.Control.ImeMode%2A> vlastnost <xref:System.Windows.Forms.ImeMode> a jenom uživatelé budou moci pro tuto konkrétní textového pole zadejte znaky ASCII.</span><span class="sxs-lookup"><span data-stu-id="cddb2-106">In such a case you can set the <xref:System.Windows.Forms.Control.ImeMode%2A> property to <xref:System.Windows.Forms.ImeMode> and users will only be able to enter ASCII characters for that particular text box.</span></span> <span data-ttu-id="cddb2-107">Výchozí hodnota <xref:System.Windows.Forms.Control.ImeMode%2A> vlastnost je <xref:System.Windows.Forms.ImeMode>, takže pokud nastavíte vlastnost pro formulář, zdědí všechny ovládací prvky na formuláři tohoto nastavení.</span><span class="sxs-lookup"><span data-stu-id="cddb2-107">The default value of the <xref:System.Windows.Forms.Control.ImeMode%2A> property is <xref:System.Windows.Forms.ImeMode>, so if you set the property for a form, all controls on the form will inherit that setting.</span></span> <span data-ttu-id="cddb2-108">Další informace najdete v tématu <xref:System.Windows.Forms.Control.ImeMode%2A> ) a <xref:System.Windows.Forms.ImeMode>.</span><span class="sxs-lookup"><span data-stu-id="cddb2-108">For more information, see <xref:System.Windows.Forms.Control.ImeMode%2A> ) and <xref:System.Windows.Forms.ImeMode>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cddb2-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="cddb2-109">See Also</span></span>  
 [<span data-ttu-id="cddb2-110">Globalizace Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cddb2-110">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
