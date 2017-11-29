---
title: "Postupy: Nastavení ovládacího prvku TextBox jen pro čtení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36116346b389dac7e9783e69d9bcd79573b4bf75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-a-textbox-control-read-only"></a><span data-ttu-id="da3c0-102">Postupy: Nastavení ovládacího prvku TextBox jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="da3c0-102">How to: Make a TextBox Control Read-Only</span></span>
<span data-ttu-id="da3c0-103">Tento příklad ukazuje, jak nakonfigurovat <xref:System.Windows.Controls.TextBox> řízení nepovolíte vstup uživatele nebo změna.</span><span class="sxs-lookup"><span data-stu-id="da3c0-103">This example shows how to configure a <xref:System.Windows.Controls.TextBox> control to not allow user input or modification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da3c0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="da3c0-104">Example</span></span>  
 <span data-ttu-id="da3c0-105">Uživatelům zabránit ve změně obsahu <xref:System.Windows.Controls.TextBox> , nastavte <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atribut **true**.</span><span class="sxs-lookup"><span data-stu-id="da3c0-105">To prevent users from modifying the contents of a <xref:System.Windows.Controls.TextBox> control, set the <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute to **true**.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <span data-ttu-id="da3c0-106"><xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> Atribut má vliv pouze na vstup uživatele; nemá vliv na nastavení v textu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] popis <xref:System.Windows.Controls.TextBox> ovládací prvek nebo text nastavují programově pomocí <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="da3c0-106">The <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute affects user input only; it does not affect text set in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] description of a <xref:System.Windows.Controls.TextBox> control, or text set programmatically through the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="da3c0-107">Výchozí hodnota <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> je **false**.</span><span class="sxs-lookup"><span data-stu-id="da3c0-107">The default value of <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> is **false**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da3c0-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="da3c0-108">See Also</span></span>  
 [<span data-ttu-id="da3c0-109">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="da3c0-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="da3c0-110">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="da3c0-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
