---
title: Výchozí instance objektů poskytované třídami My.Forms a My.WebServices
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 141f2f5f98499498d3c6732f7ae8d0abe6259ed9
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990243"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="8bc19-102">Výchozí instance objektů poskytované třídami My.Forms a My.WebServices (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bc19-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>

<span data-ttu-id="8bc19-103">Objekty [My. Forms](../../language-reference/objects/my-forms-object.md) a [My.](../../language-reference/objects/my-webservices-object.md) WebServices poskytují přístup k formulářům, zdrojům dat a webovým službám XML, které vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="8bc19-103">The [My.Forms](../../language-reference/objects/my-forms-object.md) and [My.WebServices](../../language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="8bc19-104">Poskytují přístup prostřednictvím kolekcí *výchozích instancí* každého z těchto objektů.</span><span class="sxs-lookup"><span data-stu-id="8bc19-104">They provide access through collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="8bc19-105">Výchozí instance</span><span class="sxs-lookup"><span data-stu-id="8bc19-105">Default Instances</span></span>  

 <span data-ttu-id="8bc19-106">Výchozí instance je instance třídy, která je poskytována modulem runtime a není nutné ji deklarovat a vytvořit pomocí `Dim` `New` příkazů a.</span><span class="sxs-lookup"><span data-stu-id="8bc19-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="8bc19-107">Následující příklad ukazuje, jak je možné deklarovat a vytvořit instanci <xref:System.Windows.Forms.Form> třídy s názvem a `Form1` jak teď lze získat výchozí instanci této <xref:System.Windows.Forms.Form> třídy prostřednictvím `My.Forms` .</span><span class="sxs-lookup"><span data-stu-id="8bc19-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 <span data-ttu-id="8bc19-108">`My.Forms`Objekt vrátí kolekci výchozích instancí pro každou `Form` třídu, která existuje ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="8bc19-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="8bc19-109">Podobně `My.WebServices` poskytuje výchozí instanci třídy proxy pro každou webovou službu, na kterou jste vytvořili odkaz na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8bc19-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bc19-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bc19-110">See also</span></span>

- [<span data-ttu-id="8bc19-111">My.Forms – objekt</span><span class="sxs-lookup"><span data-stu-id="8bc19-111">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="8bc19-112">My.WebServices – objekt</span><span class="sxs-lookup"><span data-stu-id="8bc19-112">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="8bc19-113">Závislost oboru názvů My na typu projektu</span><span class="sxs-lookup"><span data-stu-id="8bc19-113">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)
