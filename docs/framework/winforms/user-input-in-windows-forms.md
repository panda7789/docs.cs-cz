---
title: "Uživatelský vstup ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard input [Windows Forms], using in Windows Forms
- Windows Forms, user input
- mouse input [Windows Forms], using in Windows Forms
- keyboards [Windows Forms], keyboard input
ms.assetid: 1486075f-1e06-4c9e-82c6-f948331db6d6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c65fdca99bb12cccf70273194e3294c71a2f5a7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="user-input-in-windows-forms"></a><span data-ttu-id="096f7-102">Uživatelský vstup ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="096f7-102">User Input in Windows Forms</span></span>
<span data-ttu-id="096f7-103">Windows Forms zahrnuje uživatelského vstupu modelu na základě událostí, které jsou vyvolány při zpracování související zpráv systému Windows.</span><span class="sxs-lookup"><span data-stu-id="096f7-103">Windows Forms includes a user input model based on events that are raised while processing related Windows messages.</span></span> <span data-ttu-id="096f7-104">Témata v této části poskytují informace o myši a klávesnice vstupu uživatele, včetně příkladů kódu, které ukazují, jak provádět určité úlohy.</span><span class="sxs-lookup"><span data-stu-id="096f7-104">The topics in this section provide information on mouse and keyboard user input, including code examples that demonstrate how to perform specific tasks.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="096f7-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="096f7-105">In This Section</span></span>  
 [<span data-ttu-id="096f7-106">Uživatelský vstup ve Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="096f7-106">User Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="096f7-107">Poskytuje přehled událostí vstupu uživatele a metody, které zpracování zpráv systému Windows.</span><span class="sxs-lookup"><span data-stu-id="096f7-107">Provides an overview of user input events and the methods that process Windows messages.</span></span>  
  
 [<span data-ttu-id="096f7-108">Vstup z klávesnice ve Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="096f7-108">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="096f7-109">Obsahuje informace o zpracování, různé typy klíčů a události klávesnice zpráv klávesnice.</span><span class="sxs-lookup"><span data-stu-id="096f7-109">Provides information on keyboard message handling, the different types of keys, and the keyboard events.</span></span>  
  
 [<span data-ttu-id="096f7-110">Vstup z myši ve Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="096f7-110">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="096f7-111">Obsahuje informace o myši události a další související myši funkce, včetně ukazatele myši a zachycení myši.</span><span class="sxs-lookup"><span data-stu-id="096f7-111">Provides information on the mouse events and other mouse-related features, including mouse cursors and mouse capture.</span></span>  
  
 [<span data-ttu-id="096f7-112">Postupy: simulace událostí myši a klávesnice v kódu</span><span class="sxs-lookup"><span data-stu-id="096f7-112">How to: Simulate Mouse and Keyboard Events in Code</span></span>](../../../docs/framework/winforms/how-to-simulate-mouse-and-keyboard-events-in-code.md)  
 <span data-ttu-id="096f7-113">Ukazuje několik různých způsobů, jak prostřednictvím kódu programu Simulace myši a vstup z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="096f7-113">Demonstrates several different ways to programmatically simulate mouse and keyboard input.</span></span>  
  
 [<span data-ttu-id="096f7-114">Postupy: popisovač uživatelského vstupu událostí ve Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="096f7-114">How to: Handle User Input Events in Windows Forms Controls</span></span>](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md)  
 <span data-ttu-id="096f7-115">Představuje příklad kódu, který zpracovává většina uživatelů vstupních událostech a hlásí informace o jednotlivých událostí.</span><span class="sxs-lookup"><span data-stu-id="096f7-115">Presents a code example that handles most user input events and reports information about each event.</span></span>  
  
 [<span data-ttu-id="096f7-116">Ověřování uživatelského vstupu ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="096f7-116">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 <span data-ttu-id="096f7-117">Popisuje metody k ověření vstupu uživatele v aplikacích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="096f7-117">Describes the methods to validate user input in Windows Forms applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="096f7-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="096f7-118">Related Sections</span></span>  
 <span data-ttu-id="096f7-119">Viz také [vytváření obslužných rutin událostí v systému Windows Forms](http://msdn.microsoft.com/library/dacysss4\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="096f7-119">Also see [Creating Event Handlers in Windows Forms](http://msdn.microsoft.com/library/dacysss4\(v=vs.110\)).</span></span>
