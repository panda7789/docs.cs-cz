---
title: Ověřování složitosti hesel
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 7b2d6a81f5dc88688a469b96d56a098a2b45c59f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363681"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>Návod: Ověření, že hesla jsou složitá (Visual Basic).
Tato metoda kontroluje některé charakteristiky silného hesla a aktualizuje parametr řetězce o informace o tom, která Kontrola hesla se nezdařila.  
  
 Hesla se dají použít v zabezpečeném systému k autorizaci uživatele. Nicméně hesla musí být obtížné pro odhad neautorizovaných uživatelů. Útočníci můžou používat program pro *slovníkový útok* , který prochází všechna slova ve slovníku (nebo ve více slovnících v různých jazycích) a testuje, jestli některá slova fungují jako uživatelské heslo. Slabá hesla, například "Yankees" nebo "Mustangu", se dají rychle uhodnout. Silnější hesla, například "? L1N3vaFiNdMeyeP@sSWerd!, Je mnohem méně pravděpodobný odhadnout. Systém chráněný heslem by měl zajistit, aby si uživatelé zvolili silná hesla.  
  
 Silné heslo je složité (obsahující kombinaci velkých a malých písmen, číslic a speciálních znaků) a není to slovo. Tento příklad ukazuje, jak ověřit složitost.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a>Kompilovat kód  
 Zavolejte tuto metodu předáním řetězce, který obsahuje toto heslo.  
  
 Tento příklad vyžaduje:  
  
- Přístup ke členům <xref:System.Text.RegularExpressions> oboru názvů. Přidejte `Imports` příkaz, pokud ve svém kódu plně nekvalifikujete názvy členů. Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Zabezpečení  
 Pokud přesouváte heslo v síti, musíte pro přenos dat použít zabezpečenou metodu. Další informace najdete v tématu [zabezpečení webových aplikací ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).
  
 Přesnost funkce můžete zlepšit `ValidatePassword` přidáním dalších kontrol složitosti:  
  
- Porovnejte heslo a jeho podřetězce s uživatelským jménem, identifikátorem uživatele a slovníkem definovaným aplikací. Kromě toho považovat vizuálně podobné znaky jako ekvivalentní při provádění porovnávání. Například považovat písmena "l" a "e" za ekvivalent číslic "1" a "3".  
  
- Pokud je k dispozici pouze jeden znak velkými písmeny, ujistěte se, že se nejedná o první znak hesla.  
  
- Ujistěte se, že poslední dva znaky hesla jsou znaky písmen.  
  
- Nepovolujte hesla, ve kterých jsou všechny symboly zadány z horního řádku klávesnice.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Text.RegularExpressions.Regex>
- [Zabezpečení webové aplikace ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))
