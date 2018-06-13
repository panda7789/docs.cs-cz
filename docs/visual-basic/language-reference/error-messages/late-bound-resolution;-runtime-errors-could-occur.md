---
title: Rozpoznání s pozdní vazbou; mohlo by dojít k chybám za běhu.
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: af027b7752fdf13f1540010a8ddb681182c1b23c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588776"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="912c1-102">Rozpoznání s pozdní vazbou; mohlo by dojít k chybám za běhu.</span><span class="sxs-lookup"><span data-stu-id="912c1-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="912c1-103">Objekt je přiřazený k proměnné deklarované jako [Object – datový typ](../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="912c1-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="912c1-104">Když deklarovat proměnnou jako `Object`, musíte provést kompilátor *pozdní vazby*, což způsobí, že další operace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="912c1-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="912c1-105">Taky zpřístupňuje potenciální chyby při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="912c1-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="912c1-106">Například, pokud přiřadíte <xref:System.Windows.Forms.Form> k `Object` proměnnou a pak zkuste přístup k <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> vlastnost, modul runtime vyvolá <xref:System.MemberAccessException> protože <xref:System.Windows.Forms.Form> třída nevystavuje `NameTable` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="912c1-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="912c1-107">Pokud je deklarovat proměnnou být určitého typu, můžete provést kompilátor *časné vazby* v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="912c1-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="912c1-108">Výsledkem je lepší výkon, řízený přístup členů specifický typ a lepší čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="912c1-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="912c1-109">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="912c1-109">By default, this message is a warning.</span></span> <span data-ttu-id="912c1-110">Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="912c1-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="912c1-111">**ID chyby:** BC42017</span><span class="sxs-lookup"><span data-stu-id="912c1-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="912c1-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="912c1-112">To correct this error</span></span>  
  
-   <span data-ttu-id="912c1-113">Pokud je to možné deklarujte proměnnou být určitého typu.</span><span class="sxs-lookup"><span data-stu-id="912c1-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912c1-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="912c1-114">See Also</span></span>  
 [<span data-ttu-id="912c1-115">Statické a dynamické vazby</span><span class="sxs-lookup"><span data-stu-id="912c1-115">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [<span data-ttu-id="912c1-116">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="912c1-116">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
