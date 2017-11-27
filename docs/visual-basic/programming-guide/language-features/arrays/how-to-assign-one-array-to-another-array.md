---
title: "Postupy: Přiřazení jednoho pole ke druhému (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0dd2d678bbfdeaa6b12b5b5a4f69d0fbca8c1944
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Enum – příkaz](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Převody pole](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
