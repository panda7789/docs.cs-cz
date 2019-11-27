---
title: Definice autonomního typu
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: f8ac26577a7fbef865605a7ecf643fa733b2c2c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344919"
---
# <a name="anonymous-type-definition-visual-basic"></a>Definice autonomního typu (Visual Basic)

V reakci na deklaraci instance anonymního typu kompilátor vytvoří novou definici třídy, která obsahuje zadané vlastnosti pro daný typ.

## <a name="compiler-generated-code"></a>Kód generovaný kompilátorem

Pro následující definici `product`kompilátor vytvoří novou definici třídy obsahující vlastnosti `Name`, `Price`a `OnHand`.

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

Definice třídy obsahuje definice vlastností podobné následujícímu. Všimněte si, že pro klíčové vlastnosti není k dispozici žádná `Set` metoda. Hodnoty vlastností klíče jsou jen pro čtení.

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

Kromě toho definice anonymního typu obsahují konstruktor bez parametrů. Konstruktory, které vyžadují parametry, nejsou povoleny.

Pokud deklarace anonymního typu obsahuje alespoň jednu vlastnost klíče, definice typu přepíše tři členy zděděné z <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>a <xref:System.Object.ToString%2A>. Pokud nejsou deklarovány žádné vlastnosti klíče, bude přepsána pouze <xref:System.Object.ToString%2A>. Přepsání poskytují následující funkce:

- `Equals` vrátí `True`, pokud jsou dvě instance anonymního typu stejné instance, nebo pokud splňují následující podmínky:

  - Mají stejný počet vlastností.

  - Vlastnosti jsou deklarovány ve stejném pořadí se stejnými názvy a stejnými odvozenými typy. Porovnávání názvů nerozlišuje velká a malá písmena.

  - Nejméně jedna z vlastností je klíčová vlastnost a klíčové slovo `Key` se používá pro stejné vlastnosti.

  - Porovnání všech odpovídajících párů klíčových vlastností vrátí `True`.

    Například v následujících příkladech `Equals` vrátí `True` pouze pro `employee01` a `employee08`. Komentář před každým řádkem určuje důvod, proč se nová instance neshoduje s `employee01`.

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode` poskytuje vhodně jedinečný GetHashCode algoritmus. Algoritmus používá pouze vlastnosti klíče k výpočtu kódu hash.

- `ToString` vrátí řetězec hodnot zřetězených vlastností, jak je znázorněno v následujícím příkladu. Jsou zahrnuty vlastnosti Key i non-Key.

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

Explicitní pojmenované vlastnosti anonymního typu nejsou v konfliktu s těmito generovanými metodami. To znamená, že nemůžete použít `.Equals`, `.GetHashCode`nebo `.ToString` k pojmenování vlastnosti.

Definice anonymního typu, které obsahují alespoň jednu vlastnost klíče, také implementují rozhraní <xref:System.IEquatable%601?displayProperty=nameWithType>, kde `T` je typ anonymního typu.

> [!NOTE]
> Deklarace anonymního typu vytvoří stejný anonymní typ pouze v případě, že se vyskytují ve stejném sestavení, jejich vlastnosti mají stejné názvy a stejné odvozené typy, vlastnosti jsou deklarovány ve stejném pořadí a stejné vlastnosti jsou označeny jako vlastnosti klíče.

## <a name="see-also"></a>Viz také:

- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
