---
title: "Rozšíření šablony stylů XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8ccd1a95586bc92bcc712639eded135a69da1a36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="0aaab-102">Rozšíření šablony stylů XSLT</span><span class="sxs-lookup"><span data-stu-id="0aaab-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="0aaab-103">Tato část popisuje různé metody rozšíření funkcí XSLT.</span><span class="sxs-lookup"><span data-stu-id="0aaab-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="0aaab-104">Můžete přidat objekty rozšíření nebo parametry s využitím <xref:System.Xml.Xsl.XsltArgumentList> třídy.</span><span class="sxs-lookup"><span data-stu-id="0aaab-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="0aaab-105">Rozšíření objektů nebo parametry může být volána z této šablony.</span><span class="sxs-lookup"><span data-stu-id="0aaab-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="0aaab-106">Kromě toho můžete také vložit blocích skriptu do šablony stylů pomocí `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="0aaab-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0aaab-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0aaab-107">In This Section</span></span>  
 [<span data-ttu-id="0aaab-108">Rozšíření objektů XSLT</span><span class="sxs-lookup"><span data-stu-id="0aaab-108">XSLT Extension Objects</span></span>](../../../../docs/standard/data/xml/xslt-extension-objects.md)  
 <span data-ttu-id="0aaab-109">Popisuje použití <xref:System.Xml.Xsl.XsltArgumentList> třídy objekty rozšíření procesu XSLT.</span><span class="sxs-lookup"><span data-stu-id="0aaab-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="0aaab-110">Parametry XSLT</span><span class="sxs-lookup"><span data-stu-id="0aaab-110">XSLT Parameters</span></span>](../../../../docs/standard/data/xml/xslt-parameters.md)  
 <span data-ttu-id="0aaab-111">Popisuje použití <xref:System.Xml.Xsl.XsltArgumentList> třída proces XSLT parametry.</span><span class="sxs-lookup"><span data-stu-id="0aaab-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="0aaab-112">Msxsl:script bloky pomocí skriptu</span><span class="sxs-lookup"><span data-stu-id="0aaab-112">Script Blocks Using msxsl:script</span></span>](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="0aaab-113">Popisuje použití `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="0aaab-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0aaab-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0aaab-114">Related Sections</span></span>  
 [<span data-ttu-id="0aaab-115">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="0aaab-115">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
