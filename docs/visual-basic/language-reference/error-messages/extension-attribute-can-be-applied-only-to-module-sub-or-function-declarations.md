---
title: Atribut 'Extension' lze použít pouze v deklaracích 'Module', 'Sub' nebo 'Function'.
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 9b8f49c498699a8f7d1c4b329e82258501aa0c47
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363095"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="75b4f-102">Atribut 'Extension' lze použít pouze v deklaracích 'Module', 'Sub' nebo 'Function'.</span><span class="sxs-lookup"><span data-stu-id="75b4f-102">'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>

<span data-ttu-id="75b4f-103">Jediným způsobem, jak rozšířit datový typ v Visual Basic, je definovat metodu rozšíření uvnitř standardního modulu.</span><span class="sxs-lookup"><span data-stu-id="75b4f-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="75b4f-104">Metoda rozšíření může být `Sub` procedura nebo `Function` procedura.</span><span class="sxs-lookup"><span data-stu-id="75b4f-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="75b4f-105">Všechny metody rozšíření musí být označeny atributem rozšíření, `<Extension()>` z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="75b4f-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="75b4f-106">Volitelně může být modul, který obsahuje metodu rozšíření, označen stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="75b4f-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="75b4f-107">Žádné jiné použití atributu Extension není platné.</span><span class="sxs-lookup"><span data-stu-id="75b4f-107">No other use of the extension attribute is valid.</span></span>

<span data-ttu-id="75b4f-108">**ID chyby:** BC36550</span><span class="sxs-lookup"><span data-stu-id="75b4f-108">**Error ID:** BC36550</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="75b4f-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="75b4f-109">To correct this error</span></span>

- <span data-ttu-id="75b4f-110">Odeberte atribut Extension.</span><span class="sxs-lookup"><span data-stu-id="75b4f-110">Remove the extension attribute.</span></span>

- <span data-ttu-id="75b4f-111">Přenavrhněte své rozšíření jako metodu definovanou v ohraničujícím modulu.</span><span class="sxs-lookup"><span data-stu-id="75b4f-111">Redesign your extension as a method, defined in an enclosing module.</span></span>

## <a name="example"></a><span data-ttu-id="75b4f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="75b4f-112">Example</span></span>

<span data-ttu-id="75b4f-113">Následující příklad definuje `Print` metodu pro `String` datový typ.</span><span class="sxs-lookup"><span data-stu-id="75b4f-113">The following example defines a `Print` method for the `String` data type.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="75b4f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="75b4f-114">See also</span></span>

- [<span data-ttu-id="75b4f-115">Přehled atributů</span><span class="sxs-lookup"><span data-stu-id="75b4f-115">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="75b4f-116">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="75b4f-116">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="75b4f-117">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="75b4f-117">Module Statement</span></span>](../statements/module-statement.md)
