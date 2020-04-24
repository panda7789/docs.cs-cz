---
title: Přístup k uživatelským datům
ms.date: 07/20/2015
helpviewer_keywords:
- domain names [Visual Basic], retrieving
- data [Visual Basic], accessing user data
- My.User object [Visual Basic], tasks
- user data [Visual Basic], domain
- user names [Visual Basic], retrieving
- user data [Visual Basic], accessing
- login names [Visual Basic]
- examples [Visual Basic], accessing user data
ms.assetid: 32492a15-ee59-4a63-a1f1-9b24cc13140a
ms.openlocfilehash: 463d3bc77237482d4cd568b9558bb72cd19e7216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349206"
---
# <a name="accessing-user-data-visual-basic"></a><span data-ttu-id="3982a-102">Přístup k uživatelským datům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3982a-102">Accessing User Data (Visual Basic)</span></span>

<span data-ttu-id="3982a-103">V této části najdete témata týkající se `My.User` objektu a úkolů, které s ním můžete provádět.</span><span class="sxs-lookup"><span data-stu-id="3982a-103">This section contains topics dealing with the `My.User` object and tasks that you can accomplish with it.</span></span>  
  
 <span data-ttu-id="3982a-104">`My.User` Objekt poskytuje přístup k informacím o přihlášeném uživateli vrácením objektu, který implementuje <xref:System.Security.Principal.IPrincipal> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3982a-104">The `My.User` object provides access to information about the logged-on user by returning an object that implements the <xref:System.Security.Principal.IPrincipal> interface.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="3982a-105">Úlohy</span><span class="sxs-lookup"><span data-stu-id="3982a-105">Tasks</span></span>  
  
|<span data-ttu-id="3982a-106">Akce</span><span class="sxs-lookup"><span data-stu-id="3982a-106">To</span></span>|<span data-ttu-id="3982a-107">Seznamte se s </span><span class="sxs-lookup"><span data-stu-id="3982a-107">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="3982a-108">Získá přihlašovací jméno uživatele.</span><span class="sxs-lookup"><span data-stu-id="3982a-108">Get the user's login name</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.Name%2A>|  
|<span data-ttu-id="3982a-109">Získat název domény uživatele, pokud aplikace používá ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="3982a-109">Get the user's domain name, if the application uses Windows authentication</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.CurrentPrincipal>|  
|<span data-ttu-id="3982a-110">Určení role uživatele</span><span class="sxs-lookup"><span data-stu-id="3982a-110">Determine the user's role</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="3982a-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="3982a-111">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.User>
