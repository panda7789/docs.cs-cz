---
title: Definice autonomního typu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: c8696ef58e0177d2d2bc6e2d4731206be77a33af
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753876"
---
# <a name="anonymous-type-definition-visual-basic"></a>Definice autonomního typu (Visual Basic)

V reakci na deklarace instanci anonymního typu kompilátor vytvoří novou definici třídy, která obsahuje zadané vlastnosti pro typy.

## <a name="compiler-generated-code"></a>Kód generovaný kompilátorem

Pro následující definici `product`, kompilátor vytvoří novou definici třídy, který obsahuje vlastnosti `Name`, `Price`, a `OnHand`.

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

Definice třídy obsahuje vlastnosti definice podobný následujícímu. Všimněte si, že neexistuje žádná `Set` metodu pro klíčové vlastnosti. Hodnoty vlastnosti klíče jsou jen pro čtení.

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

Definice anonymního typu navíc obsahovat výchozí konstruktor. Konstruktory, které vyžadují parametry nejsou povoleny.

Pokud deklarace anonymního typu obsahuje alespoň jednu klíčovou vlastnost, přepíše definice typu tři členy zděděné z <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, a <xref:System.Object.ToString%2A>. Pokud jsou deklarovány žádné vlastnosti klíče, pouze <xref:System.Object.ToString%2A> je přepsána. Přepsání poskytují následující funkce:

- `Equals` Vrátí `True` Pokud dvě instance anonymního typu jsou stejnou instanci, nebo pokud nebudou splňovat následující podmínky:

  - Mají stejný počet vlastností.

  - Vlastnosti jsou deklarovány ve stejném pořadí, se stejnými názvy a stejné odvozené typy. Název porovnání nerozlišují malá a velká písmena.

  - Nejméně jedna z vlastností je klíčová vlastnost a `Key` – klíčové slovo platí stejné vlastnosti.

  - Porovnání jednotlivých odpovídající dvojice klíčů vlastnosti vrátí `True`.

    Například v následujících příkladech `Equals` vrátí `True` pouze pro `employee01` a `employee08`. Komentář před každý řádek Určuje důvod, proč novou instanci se neshoduje s `employee01`.

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode` poskytuje odpovídajícím způsobem jedinečný algoritmus GetHashCode. Tento algoritmus se používá pouze klíčové vlastnosti k výpočtu kódů hash.

- `ToString` Vrátí řetězec hodnoty zřetězených vlastností, jak je znázorněno v následujícím příkladu. Klíče a vlastnosti neklíčovým jsou zahrnuty.

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

Explicitně pojmenované vlastnosti anonymního typu nelze v konfliktu s těmito generované metody. To znamená, že nelze použít `.Equals`, `.GetHashCode`, nebo `.ToString` název vlastnosti.

Definice anonymního typu, které obsahují alespoň jeden klíčové vlastnosti také implementovat <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní, ve kterém `T` je typ anonymního typu.

> [!NOTE]
> Anonymní typ deklarace vytvoření stejné anonymního typu pouze v případě, že se objeví ve stejném sestavení, jejich vlastnosti mají stejné názvy a stejné odvodit typy, vlastnosti jsou deklarovány ve stejném pořadí a stejné vlastnosti jsou označeny jako vlastnosti klíče.

## <a name="see-also"></a>Viz také:

- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Postupy: Odvození názvů a typů v deklaracích anonymního typu vlastností](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
