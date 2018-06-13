---
title: Rozšíření šablony stylů XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff952df59dc8291b12df2b238052d4c40c834e2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568820"
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="c84c0-102">Rozšíření šablony stylů XSLT</span><span class="sxs-lookup"><span data-stu-id="c84c0-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="c84c0-103">Tato část popisuje různé metody rozšíření funkcí XSLT.</span><span class="sxs-lookup"><span data-stu-id="c84c0-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="c84c0-104">Můžete přidat objekty rozšíření nebo parametry s využitím <xref:System.Xml.Xsl.XsltArgumentList> třídy.</span><span class="sxs-lookup"><span data-stu-id="c84c0-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="c84c0-105">Rozšíření objektů nebo parametry může být volána z této šablony.</span><span class="sxs-lookup"><span data-stu-id="c84c0-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="c84c0-106">Kromě toho můžete také vložit blocích skriptu do šablony stylů pomocí `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="c84c0-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c84c0-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c84c0-107">In This Section</span></span>  
 [<span data-ttu-id="c84c0-108">Objekty rozšíření XSLT</span><span class="sxs-lookup"><span data-stu-id="c84c0-108">XSLT Extension Objects</span></span>](../../../../docs/standard/data/xml/xslt-extension-objects.md)  
 <span data-ttu-id="c84c0-109">Popisuje použití <xref:System.Xml.Xsl.XsltArgumentList> třídy objekty rozšíření procesu XSLT.</span><span class="sxs-lookup"><span data-stu-id="c84c0-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="c84c0-110">Parametry XSLT</span><span class="sxs-lookup"><span data-stu-id="c84c0-110">XSLT Parameters</span></span>](../../../../docs/standard/data/xml/xslt-parameters.md)  
 <span data-ttu-id="c84c0-111">Popisuje použití <xref:System.Xml.Xsl.XsltArgumentList> třída proces XSLT parametry.</span><span class="sxs-lookup"><span data-stu-id="c84c0-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="c84c0-112">Bloky skriptu používající element msxsl:script</span><span class="sxs-lookup"><span data-stu-id="c84c0-112">Script Blocks Using msxsl:script</span></span>](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="c84c0-113">Popisuje použití `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="c84c0-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c84c0-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c84c0-114">Related Sections</span></span>  
 [<span data-ttu-id="c84c0-115">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="c84c0-115">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
