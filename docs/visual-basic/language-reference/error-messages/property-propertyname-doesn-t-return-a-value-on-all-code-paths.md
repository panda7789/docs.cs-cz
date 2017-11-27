---
title: "Vlastnost & č. 39; &lt;propertyname&gt;& č. 39; nemá & č. 39; t vrátit hodnotu na všechny cesty kódu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords: BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c9ef5b2ac62412f5684cbc78ab6bebf6bc7b6752
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="698e3-102">Vlastnost & č. 39; &lt;propertyname&gt;& č. 39; nemá & č. 39; t vrátit hodnotu na všechny cesty kódu</span><span class="sxs-lookup"><span data-stu-id="698e3-102">Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="698e3-103">Vlastnost '\<propertyname >' nevrací hodnotu na všechny cesty kódu.</span><span class="sxs-lookup"><span data-stu-id="698e3-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="698e3-104">Výjimka odkazu s hodnotou null mohlo dojít v době běhu, když se použije výsledek.</span><span class="sxs-lookup"><span data-stu-id="698e3-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="698e3-105">Vlastnost `Get` procedura nemá alespoň jednu cestu možný prostřednictvím jeho kód, který nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="698e3-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="698e3-106">Můžete vrátit hodnotu z vlastnosti `Get` postup v některém z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="698e3-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="698e3-107">Přiřadí hodnotu pro název vlastnosti a poté proveďte `Exit Property` příkaz.</span><span class="sxs-lookup"><span data-stu-id="698e3-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
-   <span data-ttu-id="698e3-108">Přiřadí hodnotu pro název vlastnosti a poté proveďte `End Get` příkaz.</span><span class="sxs-lookup"><span data-stu-id="698e3-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
-   <span data-ttu-id="698e3-109">Zahrnout hodnotu v [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="698e3-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="698e3-110">Pokud ovládací prvek předává do `Exit Property` nebo `End Get` a nebyly přiřazeny žádnou hodnotu pro název vlastnosti `Get` postup vrátí výchozí hodnota vlastnosti datového typu.</span><span class="sxs-lookup"><span data-stu-id="698e3-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="698e3-111">Další informace najdete v tématu "Chování" v [funkce příkaz](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="698e3-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="698e3-112">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="698e3-112">By default, this message is a warning.</span></span> <span data-ttu-id="698e3-113">Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="698e3-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="698e3-114">**ID chyby:** BC42107</span><span class="sxs-lookup"><span data-stu-id="698e3-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="698e3-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="698e3-115">To correct this error</span></span>  
  
-   <span data-ttu-id="698e3-116">Zkontrolujte logika toku řízení a ujistěte se, že přiřadit hodnotu před každý příkaz, který způsobí, že vrátit.</span><span class="sxs-lookup"><span data-stu-id="698e3-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="698e3-117">Je snazší zaručit, že každý vrátit v postupu vrací hodnotu, pokud je vždy použít `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="698e3-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="698e3-118">Pokud použijete tento, poslední příkaz před `End Get` by měla být `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="698e3-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="698e3-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="698e3-119">See Also</span></span>  
 [<span data-ttu-id="698e3-120">Procedury vlastností</span><span class="sxs-lookup"><span data-stu-id="698e3-120">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="698e3-121">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="698e3-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="698e3-122">Get – příkaz</span><span class="sxs-lookup"><span data-stu-id="698e3-122">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
