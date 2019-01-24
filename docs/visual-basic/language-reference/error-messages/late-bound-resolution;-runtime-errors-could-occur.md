---
title: Rozpoznání s pozdní vazbou; mohlo by dojít k chybám za běhu.
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 9caf02907e4b6de4c2bd8de778d4ad7a9320a82b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690576"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="bc94f-102">Rozpoznání s pozdní vazbou; mohlo by dojít k chybám za běhu.</span><span class="sxs-lookup"><span data-stu-id="bc94f-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="bc94f-103">Objekt je přiřazen proměnné deklarované jako [datový typ objektu](../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="bc94f-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="bc94f-104">Pokud deklarujete proměnnou pro tu `Object`, musíte provést kompilátor *pozdní vazby*, což způsobí, že další operace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="bc94f-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="bc94f-105">Také poskytuje aplikaci potenciální běhové chyby.</span><span class="sxs-lookup"><span data-stu-id="bc94f-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="bc94f-106">Například, pokud přiřadíte <xref:System.Windows.Forms.Form> k `Object` proměnnou a pak zkuste přístup k <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> vlastnost, modul runtime vyvolá <xref:System.MemberAccessException> protože <xref:System.Windows.Forms.Form> třídy nevystavuje `NameTable` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bc94f-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="bc94f-107">Pokud deklarujete proměnnou deklarovanou určitého typu, kompilátor může provádět *časné vazby* v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="bc94f-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="bc94f-108">Výsledkem je vylepšení výkonu, řízený přístup k členům konkrétního typu a lepší čitelnost vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="bc94f-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="bc94f-109">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="bc94f-109">By default, this message is a warning.</span></span> <span data-ttu-id="bc94f-110">Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="bc94f-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="bc94f-111">**ID chyby:** BC42017</span><span class="sxs-lookup"><span data-stu-id="bc94f-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bc94f-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="bc94f-112">To correct this error</span></span>  
  
-   <span data-ttu-id="bc94f-113">Pokud je to možné deklarujte proměnnou deklarovanou určitého typu.</span><span class="sxs-lookup"><span data-stu-id="bc94f-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc94f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc94f-114">See also</span></span>
- [<span data-ttu-id="bc94f-115">Statické a dynamické vazby</span><span class="sxs-lookup"><span data-stu-id="bc94f-115">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="bc94f-116">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="bc94f-116">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
