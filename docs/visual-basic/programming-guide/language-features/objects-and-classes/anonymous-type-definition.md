---
title: Definice autonomního typu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 179fb9773fde2631666498d54894037b2bbfd087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649617"
---
# <a name="anonymous-type-definition-visual-basic"></a>Definice autonomního typu (Visual Basic)
V reakci na deklaraci instanci anonymního typu kompilátor vytvoří nové definice třídy, která obsahuje zadané vlastnosti pro typ.  
  
## <a name="compiler-generated-code"></a>Generované kompilátorem kódu  
 Pro následující definici `product`, kompilátor vytvoří nové definice třídy, která obsahuje vlastnosti `Name`, `Price`, a `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
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
  
 Definice autonomního typu navíc obsahovat výchozí konstruktor. Konstruktory, které vyžadují parametry nejsou povoleny.  
  
 Pokud deklaraci anonymního typu obsahuje alespoň jednu klíčovou vlastnost, definici typu nahradí tři členy zděděno z <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, a <xref:System.Object.ToString%2A>. Pokud jsou deklarovány žádné klíčové vlastnosti, pouze <xref:System.Object.ToString%2A> přepsána. Přepsání poskytují následující funkce:  
  
-   `Equals` Vrátí `True` Pokud dvě instance anonymního typu stejnou instanci, nebo pokud nebudou splňovat následující podmínky:  
  
    -   Mají stejný počet vlastnosti.  
  
    -   Vlastnosti jsou deklarovány ve stejném pořadí, se stejnými názvy a stejné odvozené typy. Název porovnání nerozlišují malá a velká písmena.  
  
    -   Nejméně jedna z vlastností je klíčovou vlastnost a `Key` – klíčové slovo, které se použijí na stejné vlastnosti.  
  
    -   Vrátí porovnání každé odpovídající dvojice klíčové vlastnosti `True`.  
  
     Například v následujících příkladech `Equals` vrátí `True` pouze pro `employee01` a `employee08`. Komentář před každý řádek Určuje důvod, proč nová instance neodpovídá `employee01`.  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   `GetHashcode` poskytuje správně jedinečný GetHashCode algoritmu. Algoritmus používá jenom klíčové vlastnosti vypočítat hodnotu hash.  
  
-   `ToString` vrací řetězec hodnot zřetězených vlastností, jak je znázorněno v následujícím příkladu. Klíč a neklíčovými vlastnostmi jsou zahrnuty.  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 Explicitně pojmenované vlastnosti anonymního typu nelze v konfliktu s tyto generovaného metody. To znamená, že nelze použít `.Equals`, `.GetHashCode`, nebo `.ToString` na název vlastnosti.  
  
 Definice autonomního typu, které obsahují aspoň jeden klíč vlastnost také implementace <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní, kde `T` je typ anonymního typu.  
  
> [!NOTE]
>  Deklaracích anonymního typu vytvářet stejný typ anonymní jenom v případě nastávají ve stejném sestavení, jejich vlastnosti mají stejné názvy a stejné odvozené typy, jsou ve stejném pořadí deklarované vlastnosti a stejné vlastnosti, které jsou označeny jako vlastnosti klíče.  
  
## <a name="see-also"></a>Viz také  
 [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
