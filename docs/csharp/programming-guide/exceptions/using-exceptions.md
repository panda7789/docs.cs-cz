---
title: Použití výjimek – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 4012027dc1a9bd2543d0a4195360e5f7e0586fe1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705259"
---
# <a name="using-exceptions-c-programming-guide"></a>Použití výjimek (Průvodce programováním v C#)
V C# chyby v programu za běhu jsou šířeny prostřednictvím programu pomocí mechanismu nazývaného výjimky. Výjimky jsou vyvolány kódem, který narazí na chybu a zachycen kódem, který může chybu opravit. Výjimky mohou být vyvolány za běhu množých jazyků .NET Framework common language (CLR) nebo kódem v programu. Jakmile je vyvolána výjimka, rozšíří se zásobníkvolání, dokud není nalezen `catch` příkaz pro výjimku. Nezachycené výjimky jsou zpracovány obecnou obslužnou rutinou výjimek poskytovanou systémem, který zobrazuje dialogové okno.  
  
 Výjimky jsou reprezentovány třídami odvozenými z . <xref:System.Exception> Tato třída identifikuje typ výjimky a obsahuje vlastnosti, které mají podrobnosti o výjimce. Vyvolání výjimky zahrnuje vytvoření instance třídy odvozené od výjimky, volitelně konfiguraci vlastností výjimky a následné vyvolání objektu pomocí klíčového `throw` slova. Například:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Po vyvolání výjimky za běhu zkontroluje aktuální příkaz, zda `try` je v rámci bloku. Pokud ano, `catch` všechny bloky `try` přidružené k bloku jsou kontrolovány, zda mohou zachytit výjimku. `Catch`bloky obvykle určují typy výjimek; Pokud je typ `catch` bloku stejného typu jako výjimka nebo základní třída `catch` výjimky, blok může zpracovat metodu. Například:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Pokud příkaz, který vyvolá výjimku `try` není v `try` rámci bloku nebo pokud blok, který jej obklopuje nemá `catch` odpovídající `try` blok, runtime zkontroluje volající metodu pro příkaz a `catch` bloky. Runtime pokračuje do zásobníku volání a `catch` hledá kompatibilní blok. Po `catch` nalezení a spuštění bloku je ovládací prvek předán `catch` dalšímu příkazu za tímto blokem.  
  
 Příkaz `try` může obsahovat `catch` více než jeden blok. První `catch` příkaz, který může zpracovat výjimku je proveden; všechny `catch` následující příkazy, i když jsou kompatibilní, jsou ignorovány. Proto catch bloky by měly být vždy seřazeny z nejvíce konkrétní (nebo nejvíce odvozené) na nejméně specifické. Například:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 Před `catch` spuštěním bloku za běhu zkontroluje bloky. `finally` `Finally`Bloky umožňují programátorovi vyčistit nejednoznačný stav, který by `try` mohl zůstat z přerušeného bloku, nebo uvolnit všechny externí prostředky (například grafické popisovače, připojení k databázi nebo datové proudy souborů) bez čekání na uvolňování paměti v době runtime k dokončení objektů. Například:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 Pokud `WriteByte()` vyvolalvýjimku, kód v `try` druhém bloku, který se pokusí `file.Close()` znovu otevřít soubor selže, pokud není volána, a soubor zůstane uzamčen. Vzhledem k tomu, že `finally` bloky jsou `finally` spouštěny i v případě, že je vyvolána výjimka, blok v předchozím příkladu umožňuje, aby byl soubor správně uzavřen a pomáhá vyhnout se chybě.  
  
 Pokud žádný `catch` kompatibilní blok je nalezen v zásobníku volání po vyvolání výjimky, dojde k jedné ze tří věcí:  
  
- Pokud je výjimka v rámci finalizační metody, finalizační metoda je přerušena a je volána základní finalizační metoda, pokud existuje.  
  
- Pokud zásobník volání obsahuje statický konstruktor nebo statický inicializátor pole, je vyvolána, <xref:System.TypeInitializationException> s původní výjimku přiřazenou <xref:System.Exception.InnerException%2A> vlastnosti nové výjimky.  
  
- Pokud je dosaženo začátku vlákna, vlákno je ukončeno.  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Výjimky a zpracování výjimek](./index.md)
