---
title: Definice autonomního typu (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8b5b7eba55d719c1482b7224ecffc78b776feb00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="5dec8-102">Definice autonomního typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5dec8-102">Anonymous Type Definition (Visual Basic)</span></span>
<span data-ttu-id="5dec8-103">V reakci na deklaraci instanci anonymního typu kompilátor vytvoří nové definice třídy, která obsahuje zadané vlastnosti pro typ.</span><span class="sxs-lookup"><span data-stu-id="5dec8-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>  
  
## <a name="compiler-generated-code"></a><span data-ttu-id="5dec8-104">Generované kompilátorem kódu</span><span class="sxs-lookup"><span data-stu-id="5dec8-104">Compiler-Generated Code</span></span>  
 <span data-ttu-id="5dec8-105">Pro následující definici `product`, kompilátor vytvoří nové definice třídy, která obsahuje vlastnosti `Name`, `Price`, a `OnHand`.</span><span class="sxs-lookup"><span data-stu-id="5dec8-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
 <span data-ttu-id="5dec8-106">Definice třídy obsahuje vlastnosti definice podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="5dec8-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="5dec8-107">Všimněte si, že neexistuje žádná `Set` metodu pro klíčové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5dec8-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="5dec8-108">Hodnoty vlastnosti klíče jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="5dec8-108">The values of key properties are read-only.</span></span>  
  
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
  
 <span data-ttu-id="5dec8-109">Definice autonomního typu navíc obsahovat výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="5dec8-109">In addition, anonymous type definitions contain a default constructor.</span></span> <span data-ttu-id="5dec8-110">Konstruktory, které vyžadují parametry nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="5dec8-110">Constructors that require parameters are not permitted.</span></span>  
  
 <span data-ttu-id="5dec8-111">Pokud deklaraci anonymního typu obsahuje alespoň jednu klíčovou vlastnost, definici typu nahradí tři členy zděděno z <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, a <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="5dec8-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="5dec8-112">Pokud jsou deklarovány žádné klíčové vlastnosti, pouze <xref:System.Object.ToString%2A> přepsána.</span><span class="sxs-lookup"><span data-stu-id="5dec8-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="5dec8-113">Přepsání poskytují následující funkce:</span><span class="sxs-lookup"><span data-stu-id="5dec8-113">The overrides provide the following functionality:</span></span>  
  
-   <span data-ttu-id="5dec8-114">`Equals`Vrátí `True` Pokud dvě instance anonymního typu stejnou instanci, nebo pokud nebudou splňovat následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="5dec8-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>  
  
    -   <span data-ttu-id="5dec8-115">Mají stejný počet vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5dec8-115">They have the same number of properties.</span></span>  
  
    -   <span data-ttu-id="5dec8-116">Vlastnosti jsou deklarovány ve stejném pořadí, se stejnými názvy a stejné odvozené typy.</span><span class="sxs-lookup"><span data-stu-id="5dec8-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="5dec8-117">Název porovnání nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="5dec8-117">Name comparisons are not case-sensitive.</span></span>  
  
    -   <span data-ttu-id="5dec8-118">Nejméně jedna z vlastností je klíčovou vlastnost a `Key` – klíčové slovo, které se použijí na stejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5dec8-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>  
  
    -   <span data-ttu-id="5dec8-119">Vrátí porovnání každé odpovídající dvojice klíčové vlastnosti `True`.</span><span class="sxs-lookup"><span data-stu-id="5dec8-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>  
  
     <span data-ttu-id="5dec8-120">Například v následujících příkladech `Equals` vrátí `True` pouze pro `employee01` a `employee08`.</span><span class="sxs-lookup"><span data-stu-id="5dec8-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="5dec8-121">Komentář před každý řádek Určuje důvod, proč nová instance neodpovídá `employee01`.</span><span class="sxs-lookup"><span data-stu-id="5dec8-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   <span data-ttu-id="5dec8-122">`GetHashcode`poskytuje správně jedinečný GetHashCode algoritmu.</span><span class="sxs-lookup"><span data-stu-id="5dec8-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="5dec8-123">Algoritmus používá jenom klíčové vlastnosti vypočítat hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="5dec8-123">The algorithm uses only the key properties to compute the hash code.</span></span>  
  
-   <span data-ttu-id="5dec8-124">`ToString`vrací řetězec hodnot zřetězených vlastností, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5dec8-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="5dec8-125">Klíč a neklíčovými vlastnostmi jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="5dec8-125">Both key and non-key properties are included.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 <span data-ttu-id="5dec8-126">Explicitně pojmenované vlastnosti anonymního typu nelze v konfliktu s tyto generovaného metody.</span><span class="sxs-lookup"><span data-stu-id="5dec8-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="5dec8-127">To znamená, že nelze použít `.Equals`, `.GetHashCode`, nebo `.ToString` na název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5dec8-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>  
  
 <span data-ttu-id="5dec8-128">Definice autonomního typu, které obsahují aspoň jeden klíč vlastnost také implementace <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní, kde `T` je typ anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="5dec8-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5dec8-129">Deklaracích anonymního typu vytvářet stejný typ anonymní jenom v případě nastávají ve stejném sestavení, jejich vlastnosti mají stejné názvy a stejné odvozené typy, jsou ve stejném pořadí deklarované vlastnosti a stejné vlastnosti, které jsou označeny jako vlastnosti klíče.</span><span class="sxs-lookup"><span data-stu-id="5dec8-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dec8-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="5dec8-130">See Also</span></span>  
 [<span data-ttu-id="5dec8-131">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="5dec8-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="5dec8-132">Postupy: odvození názvů a typů v deklaracích anonymního typu vlastností</span><span class="sxs-lookup"><span data-stu-id="5dec8-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
