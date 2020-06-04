---
title: Rozpoznání s pozdní vazbou; mohlo by dojít k chybám za běhu.
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: f1dc656a09eee05080356892b280a79505f3b9cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397347"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="6fa68-102">Rozpoznání s pozdní vazbou; mohlo by dojít k chybám za běhu.</span><span class="sxs-lookup"><span data-stu-id="6fa68-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="6fa68-103">Objekt je přiřazen proměnné deklarované jako [datový typ objektu](../data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="6fa68-103">An object is assigned to a variable declared to be of the [Object Data Type](../data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="6fa68-104">Pokud deklarujete proměnnou jako `Object` , kompilátor musí provést *pozdní vazbu*, což způsobí dodatečné operace za běhu.</span><span class="sxs-lookup"><span data-stu-id="6fa68-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="6fa68-105">Také zpřístupňuje vaši aplikaci potenciálním chybám za běhu.</span><span class="sxs-lookup"><span data-stu-id="6fa68-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="6fa68-106">Například pokud přiřadíte <xref:System.Windows.Forms.Form> `Object` proměnné a potom se pokusíte o přístup k <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> vlastnosti, modul runtime vyvolá výjimku, <xref:System.MemberAccessException> protože <xref:System.Windows.Forms.Form> Třída nevystavuje `NameTable` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6fa68-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="6fa68-107">Pokud deklarujete proměnnou, která má být konkrétního typu, kompilátor může provádět *počáteční vazbu* v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="6fa68-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="6fa68-108">Výsledkem je vyšší výkon, řízený přístup ke členům konkrétního typu a lepší čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="6fa68-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="6fa68-109">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="6fa68-109">By default, this message is a warning.</span></span> <span data-ttu-id="6fa68-110">Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6fa68-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="6fa68-111">**ID chyby:** BC42017</span><span class="sxs-lookup"><span data-stu-id="6fa68-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6fa68-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="6fa68-112">To correct this error</span></span>  
  
- <span data-ttu-id="6fa68-113">Pokud je to možné, deklarujte proměnnou, která má být specifického typu.</span><span class="sxs-lookup"><span data-stu-id="6fa68-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa68-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fa68-114">See also</span></span>

- [<span data-ttu-id="6fa68-115">Počáteční a pozdní vazba</span><span class="sxs-lookup"><span data-stu-id="6fa68-115">Early and Late Binding</span></span>](../../programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="6fa68-116">Deklarace proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="6fa68-116">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
