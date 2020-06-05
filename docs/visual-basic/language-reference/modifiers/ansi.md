---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 67792e52c21555bef46548e9ab0a6ebd32061071
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373197"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="e7e23-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7e23-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="e7e23-103">Určuje, že Visual Basic mají zařazovat všechny řetězce do organizace ANSI (American National Standards Institute) (ANSI) hodnoty bez ohledu na název deklarované externí procedury.</span><span class="sxs-lookup"><span data-stu-id="e7e23-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="e7e23-104">Při volání procedury definované mimo projekt, kompilátor Visual Basic nemá přístup k informacím, které potřebuje pro správné volání procedury.</span><span class="sxs-lookup"><span data-stu-id="e7e23-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="e7e23-105">Tyto informace zahrnují, kde se nachází postup, jak se identifikuje, jeho volající sekvence a návratový typ a znaková sada, kterou používá.</span><span class="sxs-lookup"><span data-stu-id="e7e23-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="e7e23-106">[Příkaz Declare](../statements/declare-statement.md) vytvoří odkaz na externí proceduru a poskytne tyto nezbytné informace.</span><span class="sxs-lookup"><span data-stu-id="e7e23-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="e7e23-107">`charsetmodifier`Část v `Declare` příkazu poskytuje znakovou sadu informace pro zařazování řetězců během volání externí procedury.</span><span class="sxs-lookup"><span data-stu-id="e7e23-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="e7e23-108">Ovlivňuje také způsob, jakým Visual Basic hledá Externí soubor pro název externí procedury.</span><span class="sxs-lookup"><span data-stu-id="e7e23-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="e7e23-109">`Ansi`Modifikátor určuje, že Visual Basic by měl zařazovat všechny řetězce do hodnot ANSI a by měl vyhledat proceduru bez úpravy jejího názvu během hledání.</span><span class="sxs-lookup"><span data-stu-id="e7e23-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="e7e23-110">Pokud není zadán modifikátor znakové sady, `Ansi` je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="e7e23-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7e23-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7e23-111">Remarks</span></span>  
 <span data-ttu-id="e7e23-112">`Ansi`V tomto kontextu lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="e7e23-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="e7e23-113">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="e7e23-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="e7e23-114">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="e7e23-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="e7e23-115">Toto klíčové slovo není podporováno.</span><span class="sxs-lookup"><span data-stu-id="e7e23-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7e23-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7e23-116">See also</span></span>

- [<span data-ttu-id="e7e23-117">Automaticky</span><span class="sxs-lookup"><span data-stu-id="e7e23-117">Auto</span></span>](auto.md)
- [<span data-ttu-id="e7e23-118">Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="e7e23-118">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="e7e23-119">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e7e23-119">Keywords</span></span>](../keywords/index.md)
