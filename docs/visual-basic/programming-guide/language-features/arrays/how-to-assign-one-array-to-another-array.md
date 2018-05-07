---
title: 'Postupy: Přiřazení jednoho pole ke druhému (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 63c7d187152fcb5ea84378c677aa687f334f63de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Postupy: Přiřazení jednoho pole ke druhému (Visual Basic)
Vzhledem k tomu, že pole jsou objekty, můžete je používat v příkazech přiřazení jako ostatní typy objektů. Proměnné pole obsahuje ukazatele na data tvořících elementy pole a informace o pořadí a délku a přiřazení zkopíruje pouze tento ukazatel.  
  
### <a name="to-assign-one-array-to-another-array"></a>K přiřazení jednoho pole ke druhému  
  
1.  Zajistěte, aby tato dvě pole element kompatibilní datové typy a stejné pořadí (počet dimenzí).  
  
2.  Příkaz standardní přiřazení použijte přiřadit zdrojové pole cílového pole. Nepostupujte podle buď název pole v závorkách.  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 Při přiřazení jednoho pole do druhého, platí následující pravidla:  
  
-   **Stejné pořadí.** Pořadí (počet dimenzí) cílového pole musí být stejná jako u zdrojové pole.  
  
     Zadané pořadí polí dvě shodné, není potřeba být stejná dimenze. Počet elementů v dané dimenzi lze změnit během přiřazení.  
  
-   **Typy elementů.** Musí mít buď obě pole *odkazují na typ* elementy nebo obě pole musí mít *typ hodnoty* elementy. Další informace najdete v tématu [typy hodnot a typy odkazu](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
    -   Pokud obě pole elementy typu hodnotu, datové typy element musí být přesně stejný. Jedinou výjimkou je, že můžete přiřadit pole `Enum` elementy na pole Základní typ, který `Enum`.  
  
    -   Pokud obě pole mít odkaz na typ elementů, element typ zdroje musí být odvozený od typu cílového elementu. Pokud to tento případ, dvě pole mají stejný vztah dědičnosti jako jejich elementů. To se označuje jako *kovariance polí*.  
  
 Kompilátor hlásí chybu, pokud výše uvedených pravidel je porušena, například pokud typy dat není kompatibilní nebo je pořadí nerovnají. Můžete přidat do kódu a ujistěte se, že tato pole jsou kompatibilní před pokusem o přiřazení zpracování chyb. Můžete také [TryCast – operátor](../../../../visual-basic/language-reference/operators/trycast-operator.md) – klíčové slovo, pokud chcete, aby se zabránilo došlo k výjimce.  
  
## <a name="see-also"></a>Viz také  
 [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Řešení potíží s poli](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Příkaz Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Převody polí](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
