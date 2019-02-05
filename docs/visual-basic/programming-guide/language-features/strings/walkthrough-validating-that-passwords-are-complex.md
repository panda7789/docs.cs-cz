---
title: Ověřování složitosti hesla (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 7bb0e3ff0d021e9923f2e1bd8ced882c6a263d15
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738562"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>Průvodce: Ověření, že hesla jsou složitá (Visual Basic)
Tato metoda zkontroluje některé vlastnosti silné heslo a aktualizuje řetězcový parametr s informacemi o tom, které kontroluje heslo selže.  
  
 Hesla je možné v zabezpečeném systému k autorizaci uživatele. Hesla musí být ale obtížné pro neoprávněné uživatele o. Útočníci můžou používat *slovníkový útok* programu, který prochází všechna slova ve slovníku (nebo více adresářů v různých jazycích) a testuje, jestli některý z slov fungovat jako heslo uživatele. Slabá hesla, jako je například "Yankees" nebo "Mustang" dají uhodnout rychle. Volba bezpečnějších hesel, jako například "? Je "L1N3vaFiNdMeyeP@sSWerd!", jsou mnohem méně pravděpodobné, že dají uhodnout. Systém chráněný heslem se ujistěte, že uživatelé vybrat silná hesla.  
  
 Silné heslo je složitý (obsahují kombinaci velká písmena, malá písmena, číselné a speciální znaky) a není u slov velká. Tento příklad ukazuje, jak ověřit složitost.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tuto metodu volejte předáním řetězce, který obsahuje toto heslo.  
  
 Tento příklad vyžaduje:  
  
-   Přístup k členům <xref:System.Text.RegularExpressions> oboru názvů. Přidat `Imports` příkazu, pokud jste nejsou kvalifikaci plně názvy členů ve vašem kódu. Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Zabezpečení  
 Pokud přesouváte hesla přes síť, budete muset použít bezpečnou metodu pro přenášení dat. Další informace najdete v tématu [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).
  
 Můžete zvýšit jeho přesnost `ValidatePassword` funkce tak, že přidáte další složitosti kontroly:  
  
-   Porovnejte heslo a jeho dílčí řetězce na jméno uživatele, identifikátor uživatele a slovníku definovaného aplikací. Kromě toho považovat za vizuálně podobné znaky ekvivalent při provádění porovnání. Například považovat za písmena "l" a "e" odpovídá číslice "1" a "3".  
  
-   Pokud existuje pouze jedno velké písmeno, ujistěte se, že se nejedná o první znak hesla.  
  
-   Ujistěte se, že poslední dva znaky heslo jsou znaky písmena.  
  
-   Nepovolit hesla, ve které jsou zadány všechny symboly z horní řádek klávesnici.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Text.RegularExpressions.Regex>
- [Zabezpečení webové aplikace ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))
