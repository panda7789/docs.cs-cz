---
title: Atribut 'Extension' lze použít pouze v deklaracích 'Module', 'Sub' nebo 'Function'.
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 2ed3a10cdf941bb8d1d7c00379736e04e8cad4d7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583186"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="30599-102">Atribut 'Extension' lze použít pouze v deklaracích 'Module', 'Sub' nebo 'Function'.</span><span class="sxs-lookup"><span data-stu-id="30599-102">'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>

<span data-ttu-id="30599-103">Jediným způsobem, jak rozšířit datový typ v Visual Basic, je definovat metodu rozšíření uvnitř standardního modulu.</span><span class="sxs-lookup"><span data-stu-id="30599-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="30599-104">Metoda rozšíření může být `Sub` procedura nebo procedura `Function`.</span><span class="sxs-lookup"><span data-stu-id="30599-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="30599-105">Všechny metody rozšíření musí být označené atributem rozšíření, `<Extension()>`, z oboru názvů <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30599-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="30599-106">Volitelně může být modul, který obsahuje metodu rozšíření, označen stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="30599-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="30599-107">Žádné jiné použití atributu Extension není platné.</span><span class="sxs-lookup"><span data-stu-id="30599-107">No other use of the extension attribute is valid.</span></span>

<span data-ttu-id="30599-108">**ID chyby:** BC36550</span><span class="sxs-lookup"><span data-stu-id="30599-108">**Error ID:** BC36550</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="30599-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="30599-109">To correct this error</span></span>

- <span data-ttu-id="30599-110">Odeberte atribut Extension.</span><span class="sxs-lookup"><span data-stu-id="30599-110">Remove the extension attribute.</span></span>

- <span data-ttu-id="30599-111">Přenavrhněte své rozšíření jako metodu definovanou v ohraničujícím modulu.</span><span class="sxs-lookup"><span data-stu-id="30599-111">Redesign your extension as a method, defined in an enclosing module.</span></span>

## <a name="example"></a><span data-ttu-id="30599-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="30599-112">Example</span></span>

<span data-ttu-id="30599-113">Následující příklad definuje metodu `Print` pro datový typ `String`.</span><span class="sxs-lookup"><span data-stu-id="30599-113">The following example defines a `Print` method for the `String` data type.</span></span>

```vb
Imports StringUtility
Imports System.Runtime.CompilerServices
Namespace StringUtility
    <Extension()>
    Module StringExtensions
        <Extension()>
        Public Sub Print (ByVal str As String)
            Console.WriteLine(str)
        End Sub
    End Module
End Namespace
```

## <a name="see-also"></a><span data-ttu-id="30599-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30599-114">See also</span></span>

- [<span data-ttu-id="30599-115">Přehled atributů</span><span class="sxs-lookup"><span data-stu-id="30599-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="30599-116">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="30599-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="30599-117">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="30599-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
