---
title: Definice autonomního typu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 9cb03eab00033c3d08b51de7524e9489198d6d76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678397"
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="6e08a-102">Definice autonomního typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e08a-102">Anonymous Type Definition (Visual Basic)</span></span>
<span data-ttu-id="6e08a-103">V reakci na deklarace instanci anonymního typu kompilátor vytvoří novou definici třídy, která obsahuje zadané vlastnosti pro typy.</span><span class="sxs-lookup"><span data-stu-id="6e08a-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>  
  
## <a name="compiler-generated-code"></a><span data-ttu-id="6e08a-104">Kód generovaný kompilátorem</span><span class="sxs-lookup"><span data-stu-id="6e08a-104">Compiler-Generated Code</span></span>  
 <span data-ttu-id="6e08a-105">Pro následující definici `product`, kompilátor vytvoří novou definici třídy, který obsahuje vlastnosti `Name`, `Price`, a `OnHand`.</span><span class="sxs-lookup"><span data-stu-id="6e08a-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
 <span data-ttu-id="6e08a-106">Definice třídy obsahuje vlastnosti definice podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="6e08a-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="6e08a-107">Všimněte si, že neexistuje žádná `Set` metodu pro klíčové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6e08a-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="6e08a-108">Hodnoty vlastnosti klíče jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="6e08a-108">The values of key properties are read-only.</span></span>  
  
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
  
 <span data-ttu-id="6e08a-109">Definice anonymního typu navíc obsahovat výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="6e08a-109">In addition, anonymous type definitions contain a default constructor.</span></span> <span data-ttu-id="6e08a-110">Konstruktory, které vyžadují parametry nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="6e08a-110">Constructors that require parameters are not permitted.</span></span>  
  
 <span data-ttu-id="6e08a-111">Pokud deklarace anonymního typu obsahuje alespoň jednu klíčovou vlastnost, přepíše definice typu tři členy zděděné z <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, a <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e08a-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="6e08a-112">Pokud jsou deklarovány žádné vlastnosti klíče, pouze <xref:System.Object.ToString%2A> je přepsána.</span><span class="sxs-lookup"><span data-stu-id="6e08a-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="6e08a-113">Přepsání poskytují následující funkce:</span><span class="sxs-lookup"><span data-stu-id="6e08a-113">The overrides provide the following functionality:</span></span>  
  
-   <span data-ttu-id="6e08a-114">`Equals` Vrátí `True` Pokud dvě instance anonymního typu jsou stejnou instanci, nebo pokud nebudou splňovat následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="6e08a-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>  
  
    -   <span data-ttu-id="6e08a-115">Mají stejný počet vlastností.</span><span class="sxs-lookup"><span data-stu-id="6e08a-115">They have the same number of properties.</span></span>  
  
    -   <span data-ttu-id="6e08a-116">Vlastnosti jsou deklarovány ve stejném pořadí, se stejnými názvy a stejné odvozené typy.</span><span class="sxs-lookup"><span data-stu-id="6e08a-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="6e08a-117">Název porovnání nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6e08a-117">Name comparisons are not case-sensitive.</span></span>  
  
    -   <span data-ttu-id="6e08a-118">Nejméně jedna z vlastností je klíčová vlastnost a `Key` – klíčové slovo platí stejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6e08a-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>  
  
    -   <span data-ttu-id="6e08a-119">Porovnání jednotlivých odpovídající dvojice klíčů vlastnosti vrátí `True`.</span><span class="sxs-lookup"><span data-stu-id="6e08a-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>  
  
     <span data-ttu-id="6e08a-120">Například v následujících příkladech `Equals` vrátí `True` pouze pro `employee01` a `employee08`.</span><span class="sxs-lookup"><span data-stu-id="6e08a-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="6e08a-121">Komentář před každý řádek Určuje důvod, proč novou instanci se neshoduje s `employee01`.</span><span class="sxs-lookup"><span data-stu-id="6e08a-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   <span data-ttu-id="6e08a-122">`GetHashcode` poskytuje odpovídajícím způsobem jedinečný algoritmus GetHashCode.</span><span class="sxs-lookup"><span data-stu-id="6e08a-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="6e08a-123">Tento algoritmus se používá pouze klíčové vlastnosti k výpočtu kódů hash.</span><span class="sxs-lookup"><span data-stu-id="6e08a-123">The algorithm uses only the key properties to compute the hash code.</span></span>  
  
-   <span data-ttu-id="6e08a-124">`ToString` Vrátí řetězec hodnoty zřetězených vlastností, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6e08a-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="6e08a-125">Klíče a vlastnosti neklíčovým jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="6e08a-125">Both key and non-key properties are included.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 <span data-ttu-id="6e08a-126">Explicitně pojmenované vlastnosti anonymního typu nelze v konfliktu s těmito generované metody.</span><span class="sxs-lookup"><span data-stu-id="6e08a-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="6e08a-127">To znamená, že nelze použít `.Equals`, `.GetHashCode`, nebo `.ToString` název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6e08a-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>  
  
 <span data-ttu-id="6e08a-128">Definice anonymního typu, které obsahují alespoň jeden klíčové vlastnosti také implementovat <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní, ve kterém `T` je typ anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="6e08a-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e08a-129">Anonymní typ deklarace vytvoření stejné anonymního typu pouze v případě, že se objeví ve stejném sestavení, jejich vlastnosti mají stejné názvy a stejné odvodit typy, vlastnosti jsou deklarovány ve stejném pořadí a stejné vlastnosti jsou označeny jako vlastnosti klíče.</span><span class="sxs-lookup"><span data-stu-id="6e08a-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e08a-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e08a-130">See also</span></span>
- [<span data-ttu-id="6e08a-131">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="6e08a-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="6e08a-132">Postupy: Odvození názvů a typů v deklaracích anonymního typu vlastností</span><span class="sxs-lookup"><span data-stu-id="6e08a-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
