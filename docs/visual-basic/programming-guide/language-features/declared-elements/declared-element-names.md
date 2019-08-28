---
title: Deklarované názvy elementu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 8a1b4869588c8dd030cf6276969063ec99b79e33
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046587"
---
# <a name="declared-element-names-visual-basic"></a>Deklarované názvy elementu (Visual Basic)
Každý deklarovaný element má název, který se označuje také jako *identifikátor*, který kód používá pro odkazování na něj.  
  
## <a name="rules"></a>Pravidly  
 Název elementu v Visual Basic musí splňovat následující pravidla:  
  
- Musí začínat znakem abecedy nebo podtržítkem (`_`).  
  
- Musí obsahovat jenom abecední znaky, desítkové číslice a podtržítka.  
  
- Musí obsahovat alespoň jeden abecední znak nebo desítkovou číslici, pokud začíná podtržítkem.  
  
- Nesmí být delší než 1023 znaků.  
  
 Omezení délky 1023 znaků platí také pro celý řetězec plně kvalifikovaného názvu, například `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 Následující příklad ukazuje některé platné názvy elementů.  
  
 `aB123__45`  
  
 `_567`  
  
 Následující příklad ukazuje některé neplatné názvy elementů. První obsahuje pouze podtržítko, druhý začíná desítkovou číslicí a třetí obsahuje neplatný znak ($).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> Názvy prvků začínající podtržítkem (`_`) nejsou součástí nezávislého [jazyka a jazykově nezávislých komponent](../../../../standard/language-independence-and-language-independent-components.md) (CLS), takže kód kompatibilní se specifikací CLS nemůže použít komponentu, která tyto názvy definuje. Podtržítko na jakékoli jiné pozici v názvu elementu však je kompatibilní se specifikací CLS.  
  
### <a name="name-length-guidelines"></a>Pokyny pro délku názvu  
 V důsledku praktického hlediska by mělo být vaše jméno co nejkratší, přičemž stále jasně identifikujete povahu prvku. To zlepšuje čitelnost kódu a zkracuje délku řádku a velikost zdrojového souboru.  
  
 Na druhé straně vaše jméno by nemělo být tak krátké, že není dostatečně důležité, co element představuje a jak ho váš kód používá. To je důležité pro čitelnost kódu. Pokud se někdo jiný snaží ho pochopit, nebo pokud si ho po jeho zapsání sami napíšete, můžete vhodný název prvku ušetřit značnou dobu.  
  
## <a name="escaped-names"></a>Řídicí názvy  
 Obecně platí, že název elementu nesmí odpovídat žádnému z klíčových slov rezervovaných Visual Basic, například `Case` nebo `Friend`. Můžete však definovat *řídicí název*, který je uzavřen hranatými závorkami (`[ ]`). Název řídicího panelu může odpovídat libovolnému klíčovému slovu Visual Basic, protože hranaté závorky odstraňují jakoukoli nejednoznačnost. Hranaté závorky můžete použít také při odkazování na název později v kódu.  
  
 Obecně byste měli používat řídicí názvy pouze v případě, že:  
  
- Váš kód se migruje z předchozí verze Visual Basic, která nerezervovala klíčové slovo, které se používá jako název; ani  
  
- Pracujete s kódem napsaným v jiném jazyce, ve kterém dané klíčové slovo není rezervované.  
  
 V opačném případě byste měli zvážit přejmenování elementu, je-li jeho název v konfliktu s klíčovým slovem. Integrované vývojové prostředí (IDE) poskytuje snadný způsob, jak to provést. Další informace najdete v tématu [](/visualstudio/vb-ide/refactoring-vb)refaktoring.  
  
## <a name="case-sensitivity-in-names"></a>Rozlišování velkých a malých písmen v názvech  
 Názvy elementů v Visual Basic rozlišují malá a velká písmena. To znamená, že když kompilátor Porovná dva názvy, které se liší pouze v abecedním případě, interpretuje je jako stejný název. Například zvažuje `ABC` a `abc` odkazuje na stejný deklarovaný element.  
  
 Modul CLR (Common Language Runtime) však používá vazby s rozlišováním velkých a malých písmen. Proto při vytváření sestavení nebo knihovny DLL a zpřístupnění pro jiná sestavení, vaše jména nebudou rozlišovat velká a malá písmena. Například pokud definujete třídu s názvem `ABC`a další sestavení využívají třídu pomocí modulu CLR (Common Language Runtime), musí odkazovat na prvek jako. `ABC` Pokud následně znovu zkompilujete třídu a změníte název prvku na `abc`, další sestavení, která používají vaši třídu, již nebudou mít přístup k tomuto prvku. Proto při vydání aktualizované verze sestavení byste neměli měnit abecední případ všech veřejných prvků.  
  
## <a name="names-and-locales"></a>Názvy a národní prostředí  
 Porovnání názvů je nezávislé na národním prostředí. Pokud se dva názvy shodují v jednom národním prostředí, je zaručeno, že budou odpovídat ve všech národních prostředích.  
  
## <a name="see-also"></a>Viz také:

- [Deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Příkazy](../../../../visual-basic/language-reference/statements/index.md)
