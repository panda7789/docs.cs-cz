---
title: 'Postupy: Přiřazení jednoho pole ke druhému'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: be5337e36c2cc7ad9f9b32182b8575ac66bb4a50
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351894"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Postupy: Přiřazení jednoho pole ke druhému (Visual Basic)

Vzhledem k tomu, že pole jsou objekty, můžete je použít v příkazech přiřazení jako jiné typy objektů. Proměnná pole obsahuje ukazatel na data tvořící prvky pole a informace o rozměrech a délce a přiřazení kopíruje pouze tento ukazatel.

### <a name="to-assign-one-array-to-another-array"></a>Přiřazení jednoho pole k jinému poli

1. Zajistěte, aby obě pole měly stejný rozměr (počet rozměrů) a kompatibilní datové typy prvků.

2. Použijte standardní příkaz přiřazení pro přiřazení zdrojového pole k cílovému poli. Neprovádějte žádné názvy polí pomocí závorek.

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

Když přiřadíte jedno pole k druhému, platí následující pravidla:

- **Stejné pořadí.** Rozměr (počet rozměrů) cílového pole musí být stejný jako zdroj pole.

  Za předpokladu, že je pořadí dvou polí stejné, dimenze nemusí být stejné. Počet prvků v dané dimenzi se může během přiřazení změnit.

- **Typy prvků.** Obě pole musí mít elementy *typu odkazu* , nebo obě pole musí mít elementy *typu hodnoty* . Další informace naleznete v tématu [typy hodnot a typy odkazů](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).

  - Pokud mají obě pole elementy typu hodnoty, musí být datové typy elementu přesně stejné. Jedinou výjimkou je, že můžete přiřadit pole `Enum` prvků k poli základního typu, který `Enum`.

  - Pokud mají obě pole elementy typu odkazu, typ zdrojového elementu musí být odvozen od typu cílového elementu. V takovém případě mají dvě pole stejný vztah dědičnosti jako jejich prvky. Tato metoda se nazývá *kovariance pole*.

Kompilátor ohlásí chybu, pokud jsou uvedená pravidla porušena, například pokud nejsou datové typy kompatibilní nebo pořadí nerovnosti. Do kódu můžete přidat zpracování chyb, abyste se ujistili, že jsou pole kompatibilní před pokusem o přiřazení. Klíčové slovo [operátoru TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md) můžete použít také v případě, že chcete zabránit vyvolání výjimky.

## <a name="see-also"></a>Viz také:

- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Řešení potíží s poli](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Příkaz Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Převody polí](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
