---
title: Datový typ objektu
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: e9b1da5a88c12e0d883c3afe63be98c3fa3e9173
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591616"
---
# <a name="object-data-type"></a>Datový typ objektu
Obsahuje adresy, které odkazují na objekty. Všechny odkaz (řetězec, pole, třídu nebo rozhraní) můžete přiřadit `Object` proměnné. `Object` Proměnné najdete také dat jakéhokoli typu hodnoty (numerickou `Boolean`, `Char`, `Date`, struktury nebo výčtové).  
  
## <a name="remarks"></a>Poznámky  
 `Object` Datový typ může ukazovat na data jakéhokoli datového typu, včetně všechny instance objektu rozpozná vaší aplikace. Použití `Object` jaké datový typ proměnné může ukazovat Pokud si nejste jisti v době kompilace.  
  
 Výchozí hodnota `Object` je `Nothing` (odkaz s hodnotou null).  
  
## <a name="data-types"></a>Datové typy  
 Můžete přiřadit proměnné, konstanta nebo výraz jakýkoli datový typ pro `Object` proměnné. Určit typ dat `Object` proměnná aktuálně odkazuje, můžete použít <xref:System.Type.GetTypeCode%2A> metodu <xref:System.Type?displayProperty=nameWithType> třídy. Toto dokládá následující příklad.  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 `Object` Datový typ je typ odkazu. Však zpracovává jazyka Visual Basic `Object` jako typ hodnoty odkazuje na datový typ hodnoty proměnné.  
  
## <a name="storage"></a>Úložiště  
 Ať datový typ, který odkazuje na, `Object` proměnná neobsahuje hodnotu dat sám sebe, ale spíš ukazatel na hodnotu. Vždy používá čtyři bajtů v paměti počítače, ale nezahrnuje úložiště pro data představující hodnotu proměnné. Z důvodu kód, který používá ukazatele vyhledejte data `Object` proměnné, která uchovává typů hodnot se nepatrně pomalejší přístup než explicitně typové proměnné.  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Spolupráce aspekty.** Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, že typy ukazatelů v jiných prostředích nejsou kompatibilní s jazykem Visual Basic `Object` typu.  
  
-   **Výkon.** Proměnné deklarovat s `Object` typ je dostatečně flexibilní, aby obsahovat odkaz na libovolného objektu. Ale při vyvolání metody nebo vlastnosti na tuto proměnnou, vždy platit *pozdní vazby* (za běhu). Chcete-li vynutit *časné vazby* (v době kompilace) a vyšší výkon, deklarovat proměnnou s názvem určité třídy nebo přetypovat na typ konkrétní data.  
  
     Po deklarování proměnné objektu zkuste použít konkrétní – třída typu, například <xref:System.OperatingSystem>, místo zobecněný `Object` typu. Většina určité třídy, které jsou k dispozici, jako byste měli použít také <xref:System.Windows.Forms.TextBox> místo <xref:System.Windows.Forms.Control>tak, aby jeho vlastnosti a metody k dispozici. Obvykle můžete používat **třídy** v seznamu **Prohlížeč objektů** najít názvy dostupných tříd.  
  
-   **Rozšíření.** Všechny datové typy a všechny typy odkazu rozšíří do `Object` datového typu. To znamená, že můžete převést do libovolného typu `Object` bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
     Ale pokud převod mezi typy hodnot a `Object`, jazyka Visual Basic provádí operace názvem *zabalení* a *rozbalení*, ujistěte se, které provádění pomalejší.  
  
-   **Znaky typu.** `Object` nemá žádnou – znak typu literálu nebo – znak typu identifikátoru.  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.Object?displayProperty=nameWithType> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ilustruje `Object` proměnné odkazující na instanci objektu.  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Object>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Postupy: Určení, zda dva objekty spolu souvisí](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Postupy: Určení, zda dva objekty jsou identické](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
