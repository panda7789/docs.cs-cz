---
title: Řešení potíží s obslužnými rutinami zděděných událostí
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: fd2ef1c25233cc1eaad6bcde68923688393b471d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345109"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="c34e5-102">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c34e5-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="c34e5-103">This topic lists common issues that arise with event handlers in inherited components.</span><span class="sxs-lookup"><span data-stu-id="c34e5-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="c34e5-104">Procedury</span><span class="sxs-lookup"><span data-stu-id="c34e5-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="c34e5-105">Code in Event Handler Executes Twice for Every Call</span><span class="sxs-lookup"><span data-stu-id="c34e5-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="c34e5-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span><span class="sxs-lookup"><span data-stu-id="c34e5-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="c34e5-107">The method in the base class is already associated with the event and will fire accordingly.</span><span class="sxs-lookup"><span data-stu-id="c34e5-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="c34e5-108">Remove the `Handles` clause from the inherited method.</span><span class="sxs-lookup"><span data-stu-id="c34e5-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="c34e5-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span><span class="sxs-lookup"><span data-stu-id="c34e5-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c34e5-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c34e5-110">See also</span></span>

- [<span data-ttu-id="c34e5-111">Události</span><span class="sxs-lookup"><span data-stu-id="c34e5-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
