---
title: 'Postupy: Přiřazení jednoho pole ke druhému (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 834dad07ec1f4116aca72a184ccffc664d0a42ed
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835281"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Postupy: Přiřazení jednoho pole ke druhému (Visual Basic)
Protože pole jsou objekty, které lze využít v přiřazovací příkazy jako ostatní typy objektů. Proměnné pole tvořící prvky pole a informace o počet rozměrů a délka dat obsahuje ukazatel a přiřazení zkopíruje pouze tento ukazatel.  
  
### <a name="to-assign-one-array-to-another-array"></a>K přiřazení jednoho pole ke druhému  
  
1.  Ujistěte se, že dvě pole mají stejné pořadí (počet rozměrů) a kompatibilní element datové typy.  
  
2.  Použijte standardní přiřazovací příkaz přiřaďte pole zdrojového do cílového pole. Nepostupujte podle buď název pole v závorkách.  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 Při přiřazení jednoho pole do jiného, platí následující pravidla:  
  
-   **Stejné rozměry.** Rozměr (počet rozměrů) cílového pole musí být stejné jako u zdrojového pole.  
  
     Pokud jsou stejné rozměry dvě pole, není potřeba rovnat dimenze. Během přiřazování můžete změnit počet prvků v dané dimenzi.  
  
-   **Typy elementů.** Buď obě pole musí mít *odkazovat na typ* elementy nebo obě pole musí mít *typ hodnoty* elementy. Další informace najdete v tématu [typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
    -   Pokud obě pole mají prvky typu hodnoty, element datové typy, které musí být přesně stejný. Jedinou výjimkou je, že můžete přiřadit pole `Enum` prvky do pole Základní typ, který `Enum`.  
  
    -   Pokud obě pole mít odkaz na typ prvků, typ zdrojového prvku musí být odvozen z typu cílového elementu. Pokud tomu tak, máte dvě pole stejné relaci dědičnosti jako jejich prvky. Tento postup se nazývá *kovariance polí*.  
  
 Kompilátor hlásí chybu, pokud se výše uvedených pravidel se poruší, například pokud datové typy, které nejsou kompatibilní, nebo je pořadí nerovnost. Můžete přidat do vašeho kódu, abyste měli jistotu, že tato pole jsou kompatibilní před pokusem o přiřazení pro zpracování chyb. Můžete také použít [TryCast – operátor](../../../../visual-basic/language-reference/operators/trycast-operator.md) – klíčové slovo, pokud chcete, aby se zabránilo došlo k výjimce.  
  
## <a name="see-also"></a>Viz také:

- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Řešení potíží s poli](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Příkaz Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Převody polí](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
