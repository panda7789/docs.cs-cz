---
title: Datový typ objektu (Visual Basic)
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
ms.openlocfilehash: 5a37b571e0600927e0e50fdb1a63bcf8ef194d72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617535"
---
# <a name="object-data-type"></a>Datový typ objektu
Obsahuje adresy, které odkazují na objekty. Jakýkoli odkaz na typ (řetězec, pole, třídy nebo rozhraní) můžete přiřadit `Object` proměnné. `Object` Proměnné lze také odkazovat na data libovolného typu hodnoty (číselné, `Boolean`, `Char`, `Date`, struktury nebo výčet).  
  
## <a name="remarks"></a>Poznámky  
 `Object` Datový typ může odkazovat na data z libovolného datového typu, včetně všechny instance objektu rozpozná vaší aplikace. Použití `Object` Pokud si nejste jisti v době kompilace, jaký datový typ proměnné může ukazovat na.  
  
 Výchozí hodnota `Object` je `Nothing` (odkaz s hodnotou null).  
  
## <a name="data-types"></a>Datové typy  
 Můžete přiřadit proměnné, konstanty nebo výrazu libovolného datového typu pro `Object` proměnné. Určit typ dat `Object` proměnná aktuálně odkazuje, můžete použít <xref:System.Type.GetTypeCode%2A> metodu <xref:System.Type?displayProperty=nameWithType> třídy. Toto dokládá následující příklad.  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 `Object` Datový typ je typ odkazu. Však zpracovává jazyka Visual Basic `Object` proměnné jako typ hodnoty, když se odkazuje na datový typ hodnoty.  
  
## <a name="storage"></a>Úložiště  
 Jakýkoli datový typ, na který odkazuje, `Object` proměnné samotné, ale spíše ukazatel na hodnotu neobsahuje hodnotu data. Vždy používá čtyři bajty v paměti počítače, ale nezahrnuje úložiště pro data představující hodnotu proměnné. Z důvodu kód, který používá ukazatel vyhledejte data `Object` proměnné obsahující typy hodnot jsou o něco pomalejší než explicitně přístup k zadané proměnné.  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Spolupráce aspekty.** Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework, například objekty automatizace nebo COM, mějte na paměti, že typy ukazatelů v jiných prostředích nejsou kompatibilní s jazykem Visual Basic `Object` typu.  
  
-   **Výkon.** Proměnná deklarovaná pomocí `Object` typ je dostatečně flexibilní, aby obsahují odkaz na libovolný objekt. Nicméně při vyvolání metody nebo vlastnosti na tyto proměnné se vždy vynakládají *pozdní vazby* (za běhu). Chcete-li vynutit *časné vazby* (v době kompilace) a lepšího výkonu, deklarujte proměnnou s názvem určité třídy nebo přetypován na určitý datový typ.  
  
     Při deklaraci proměnné objektu, zkuste použít určitý typ třídy, například <xref:System.OperatingSystem>, místo zobecněný `Object` typu. By měl také použít k dispozici, například na třídu nejspecifičtější <xref:System.Windows.Forms.TextBox> místo <xref:System.Windows.Forms.Control>, aby přístup k jeho vlastnosti a metody. Můžete obvykle použít **třídy** v seznamu **prohlížeče objektů** najít názvy tříd k dispozici.  
  
-   **Rozšíření.** Všechny typy dat a všechny typy odkazů rozšířit na `Object` datového typu. To znamená, že lze převést libovolný typ `Object` aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
     Ale při převodu mezi typy hodnot a `Object`, Visual Basic provádí operace volat *zabalení* a *rozbalení*, ujistěte se, které provádění pomalejší.  
  
-   **Znaky typu.** `Object` nemá žádný – znak typu literálu nebo – znak typu identifikátoru.  
  
-   **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Object?displayProperty=nameWithType> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `Object` proměnná odkazuje na instanci objektu.  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Object>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Postupy: Určení, zda dva objekty souvisejí](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Postupy: Určení, zda dva objekty jsou identické](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
