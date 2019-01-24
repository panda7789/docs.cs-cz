---
title: 'Postupy: Pomocí mailto: k odeslání e-mailu ze stránky'
ms.date: 03/30/2017
helpviewer_keywords:
- 'sending mail from pages with mailto:'
- mailto:, sending mail from pages
- mail [WPF], sending from pages
ms.assetid: b64b9518-df17-4232-94f2-455a4f77ee48
ms.openlocfilehash: 34571fd7df6c75cb5b71db0ccc5565ebaae5badb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710765"
---
# <a name="how-to-use-mailto-to-send-mail-from-a-page"></a><span data-ttu-id="4e0af-102">Postupy: Pomocí mailto: k odeslání e-mailu ze stránky</span><span class="sxs-lookup"><span data-stu-id="4e0af-102">How to: Use mailto: to Send Mail From a Page</span></span>
<span data-ttu-id="4e0af-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Documents.Hyperlink> ve spojení s **mailto:**[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e0af-103">This example shows how to use <xref:System.Windows.Documents.Hyperlink> in conjunction with a **mailto:**[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e0af-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e0af-104">Example</span></span>  
 <span data-ttu-id="4e0af-105">Následující kód ukazuje, jak používat **mailto:** [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] otevřete nové okno e-mailu, který obsahuje e-mailovou adresu, a e-mailové adresy a předmětu a e-mailovou adresu, na základě práv subjektů a textu.</span><span class="sxs-lookup"><span data-stu-id="4e0af-105">The following code shows how to use a **mailto:**[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] to open a new mail window that contains an email address, and email address and a subject, and an email address, subject, and body.</span></span>  
  
 [!code-xaml[HOWTONavigationMailToSnippet#MailToMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationMailToSnippet/CS/HomePage.xaml#mailtomarkup)]  
  
## <a name="see-also"></a><span data-ttu-id="4e0af-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e0af-106">See also</span></span>
- [<span data-ttu-id="4e0af-107">Sbalení URI v technologii WPF</span><span class="sxs-lookup"><span data-stu-id="4e0af-107">Pack URIs in WPF</span></span>](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
