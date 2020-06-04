---
title: Definice anonymního typu
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 952eb295cc71eab5d0ad6e18f2b697a9b701b434
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404898"
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="55cf6-102">Definice autonomního typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55cf6-102">Anonymous Type Definition (Visual Basic)</span></span>

<span data-ttu-id="55cf6-103">V reakci na deklaraci instance anonymního typu kompilátor vytvoří novou definici třídy, která obsahuje zadané vlastnosti pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="55cf6-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="55cf6-104">Kód generovaný kompilátorem</span><span class="sxs-lookup"><span data-stu-id="55cf6-104">Compiler-Generated Code</span></span>

<span data-ttu-id="55cf6-105">Pro následující definici `product` vytvoří kompilátor novou definici třídy, která obsahuje vlastnosti `Name` , `Price` a `OnHand` .</span><span class="sxs-lookup"><span data-stu-id="55cf6-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

<span data-ttu-id="55cf6-106">Definice třídy obsahuje definice vlastností podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="55cf6-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="55cf6-107">Všimněte si, že pro klíčové vlastnosti není k dispozici žádná `Set` metoda.</span><span class="sxs-lookup"><span data-stu-id="55cf6-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="55cf6-108">Hodnoty vlastností klíče jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="55cf6-108">The values of key properties are read-only.</span></span>

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

<span data-ttu-id="55cf6-109">Kromě toho definice anonymního typu obsahují konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="55cf6-109">In addition, anonymous type definitions contain a parameterless constructor.</span></span> <span data-ttu-id="55cf6-110">Konstruktory, které vyžadují parametry, nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="55cf6-110">Constructors that require parameters are not permitted.</span></span>

<span data-ttu-id="55cf6-111">Pokud deklarace anonymního typu obsahuje alespoň jednu vlastnost klíče, definice typu přepíše tři členy zděděné z <xref:System.Object> : <xref:System.Object.Equals%2A> , <xref:System.Object.GetHashCode%2A> a <xref:System.Object.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="55cf6-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="55cf6-112">Pokud nejsou deklarovány žádné vlastnosti klíče, <xref:System.Object.ToString%2A> je pouze přepsána.</span><span class="sxs-lookup"><span data-stu-id="55cf6-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="55cf6-113">Přepsání poskytují následující funkce:</span><span class="sxs-lookup"><span data-stu-id="55cf6-113">The overrides provide the following functionality:</span></span>

- <span data-ttu-id="55cf6-114">`Equals`Vrátí `True` , zda jsou dvě instance anonymního typu stejné instance, nebo pokud splňují následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="55cf6-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>

  - <span data-ttu-id="55cf6-115">Mají stejný počet vlastností.</span><span class="sxs-lookup"><span data-stu-id="55cf6-115">They have the same number of properties.</span></span>

  - <span data-ttu-id="55cf6-116">Vlastnosti jsou deklarovány ve stejném pořadí se stejnými názvy a stejnými odvozenými typy.</span><span class="sxs-lookup"><span data-stu-id="55cf6-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="55cf6-117">Porovnávání názvů nerozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="55cf6-117">Name comparisons are not case-sensitive.</span></span>

  - <span data-ttu-id="55cf6-118">Nejméně jedna z vlastností je klíčová vlastnost a `Key` klíčové slovo se používá pro stejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="55cf6-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>

  - <span data-ttu-id="55cf6-119">Vrátí se porovnání každého odpovídajícího páru vlastností klíče `True` .</span><span class="sxs-lookup"><span data-stu-id="55cf6-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>

    <span data-ttu-id="55cf6-120">Například v následujících příkladech `Equals` vrátí `True` pouze pro `employee01` a `employee08` .</span><span class="sxs-lookup"><span data-stu-id="55cf6-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="55cf6-121">Komentář před každým řádkem určuje důvod, proč se nová instance neshoduje `employee01` .</span><span class="sxs-lookup"><span data-stu-id="55cf6-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- <span data-ttu-id="55cf6-122">`GetHashcode`poskytuje vhodně jedinečný GetHashCode algoritmus.</span><span class="sxs-lookup"><span data-stu-id="55cf6-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="55cf6-123">Algoritmus používá pouze vlastnosti klíče k výpočtu kódu hash.</span><span class="sxs-lookup"><span data-stu-id="55cf6-123">The algorithm uses only the key properties to compute the hash code.</span></span>

- <span data-ttu-id="55cf6-124">`ToString`Vrátí řetězec hodnot zřetězených vlastností, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="55cf6-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="55cf6-125">Jsou zahrnuty vlastnosti Key i non-Key.</span><span class="sxs-lookup"><span data-stu-id="55cf6-125">Both key and non-key properties are included.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

<span data-ttu-id="55cf6-126">Explicitní pojmenované vlastnosti anonymního typu nejsou v konfliktu s těmito generovanými metodami.</span><span class="sxs-lookup"><span data-stu-id="55cf6-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="55cf6-127">To znamená, že nemůžete použít `.Equals` , `.GetHashCode` nebo `.ToString` k pojmenování vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="55cf6-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>

<span data-ttu-id="55cf6-128">Definice anonymního typu, které obsahují alespoň jednu vlastnost klíče, také implementují <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní, kde `T` je typ anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="55cf6-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>

> [!NOTE]
> <span data-ttu-id="55cf6-129">Deklarace anonymního typu vytvoří stejný anonymní typ pouze v případě, že se vyskytují ve stejném sestavení, jejich vlastnosti mají stejné názvy a stejné odvozené typy, vlastnosti jsou deklarovány ve stejném pořadí a stejné vlastnosti jsou označeny jako vlastnosti klíče.</span><span class="sxs-lookup"><span data-stu-id="55cf6-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="55cf6-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="55cf6-130">See also</span></span>

- [<span data-ttu-id="55cf6-131">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="55cf6-131">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="55cf6-132">Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu</span><span class="sxs-lookup"><span data-stu-id="55cf6-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
