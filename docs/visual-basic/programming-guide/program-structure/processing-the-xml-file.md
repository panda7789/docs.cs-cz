---
title: Zpracování souboru XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 81d2c8d305e828b2963a0af9d97ec35b1745197a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398328"
---
# <a name="processing-the-xml-file-visual-basic"></a>Zpracování souboru XML (Visual Basic)
Kompilátor generuje řetězec ID pro každou konstrukci v kódu, který je označen pro generování dokumentace. (Informace o tom, jak označit svůj kód, naleznete v tématu [značky komentářů XML](../../language-reference/xmldoc/index.md).) Řetězec ID jednoznačně identifikuje konstrukci. Programy, které zpracovávají soubor XML, mohou pomocí řetězce ID identifikovat odpovídající .NET Framework metadat nebo položku reflexe.  
  
 Soubor XML není hierarchická reprezentace vašeho kódu; Jedná se o plochý seznam s vygenerovaným ID pro každý prvek.  
  
 Kompilátor při generování řetězců ID sleduje následující pravidla:  
  
- V řetězci není vložen prázdný znak.  
  
- První část řetězce ID identifikuje druh identifikovaného člena s jedním znakem následovaným dvojtečkou. Používají se následující typy členů.  
  
|Znak|Description|  
|---|---|  
|N|namespace<br /><br /> Do oboru názvů nemůžete přidávat komentáře k dokumentaci, ale můžete na ně CREF odkazy, kde se podporují.|  
|T|zadejte: `Class` , `Module` , `Interface` , `Structure` , `Enum` ,`Delegate`|  
|F|dílčí`Dim`|  
|P|vlastnost: `Property` (včetně výchozích vlastností)|  
|M|Metoda: `Sub` , `Function` , `Declare` ,`Operator`|  
|E|událostí`Event`|  
|!|řetězec chyby<br /><br /> Zbytek řetězce poskytuje informace o chybě. Kompilátor Visual Basic generuje informace o chybě pro odkazy, které nelze přeložit.|  
  
- Druhá část `String` je plně kvalifikovaný název položky začínající v kořenu oboru názvů. Název položky, její ohraničující typ (y) a obor názvů jsou odděleny tečkami. Pokud název samotné položky obsahuje tečky, nahradí se znakem čísla (#). Předpokládá se, že žádná položka nemá znak čísla přímo v názvu. Například plně kvalifikovaný název `String` konstruktoru by byl `System.String.#ctor` .  
  
- V případě vlastností a metod, pokud jsou argumenty metody, seznam argumentů uzavřený v závorkách následuje. Pokud nejsou žádné argumenty, nejsou k dispozici žádné závorky. Argumenty jsou odděleny čárkami. Kódování každého argumentu následuje přímo, jak je kódováno v signatuře .NET Framework.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak jsou generovány řetězce ID pro třídu a její členy.  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>Viz také

- [-doc](../../reference/command-line-compiler/doc.md)
- [Postupy: Vytvoření dokumentace XML](how-to-create-xml-documentation.md)
