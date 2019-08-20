---
title: Použití výjimek – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 8d0fe4b8c2ba3e64aa7ee34fc9d02b29bda5c017
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590166"
---
# <a name="using-exceptions-c-programming-guide"></a>Použití výjimek (Průvodce programováním v C#)
V C#systému jsou chyby v programu v době běhu šířeny prostřednictvím programu pomocí mechanismu nazývaného výjimky. Výjimky jsou vyvolány kódem, který zaznamená chybu a zachycena kódem, který může chybu opravit. Výjimky mohou být vyvolány .NET Framework Common Language Runtime (CLR) nebo pomocí kódu v programu. Jakmile je vyvolána výjimka, rozšíří zásobník volání, dokud `catch` nebude nalezen příkaz pro výjimku. Nezachycené výjimky jsou zpracovávány pomocí obecné obslužné rutiny výjimky poskytované systémem, který zobrazuje dialogové okno.  
  
 Výjimky jsou reprezentovány třídami <xref:System.Exception>odvozenými z. Tato třída identifikuje typ výjimky a obsahuje vlastnosti, které obsahují podrobnosti o výjimce. Vyvolání výjimky zahrnuje vytvoření instance třídy odvozené od výjimky, volitelně konfiguraci vlastností výjimky a následné vyvolání objektu pomocí `throw` klíčového slova. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Po vyvolání výjimky modul runtime zkontroluje aktuální příkaz a zjistí, zda je v rámci `try` bloku. Pokud je, jsou zkontrolovány všechny `catch` bloky přidružené `try` k bloku, aby bylo vidět, zda mohou zachytit výjimku. `Catch`bloky obvykle určují typy výjimek; Pokud je typ `catch` bloku shodný s typem výjimky nebo základní třídou výjimky `catch` , může blok zpracovat metodu. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Pokud příkaz, který vyvolá `try` výjimku, není uvnitř bloku nebo `try` Pokud blok, který ho obklopuje, nemá odpovídající `catch` blok, modul runtime zkontroluje volající metodu pro `try` příkaz a `catch` bloky. Modul runtime pokračuje v zásobníku volání a hledá kompatibilní `catch` blok. Po nalezení a provedení `catch` blokujeovládacíprvekpředándalšímupříkazupotomtobloku.`catch`  
  
 Příkaz může obsahovat více než jeden `catch` blok. `try` Je proveden `catch` první příkaz, který může zpracovat výjimku; všechny následující `catch` příkazy, i když jsou kompatibilní, jsou ignorovány. Proto by bloky catch měly být vždy řazeny z nejvíce specifického (nebo nejvíce odvozeného) na nejméně konkrétní. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 Před provedením `finally` bloku modul runtime vyhledá bloky. `catch` `Finally`bloky umožňují programátorovi vyčistit libovolný dvojznačný stav, který by mohl zůstat z přerušeného `try` bloku, nebo uvolnit jakékoli externí prostředky (jako jsou grafické popisovače, databázová připojení nebo datové proudy souborů) bez čekání na uvolnění paměti. kolektor v modulu runtime pro finalizaci objektů. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 Pokud `WriteByte()` vyvolal výjimku, kód v druhém `try` bloku, který se pokusí znovu otevřít soubor, selže, pokud `file.Close()` není volán, a soubor by zůstal uzamčen. Vzhledem `finally` k tomu, že jsou bloky spouštěny i v případě `finally` , že dojde k výjimce, blok v předchozím příkladu umožňuje, aby se soubor správně zavřel, a pomáhá vyhnout se chybě.  
  
 Pokud v zásobníku `catch` volání není po vyvolání výjimky nalezen žádný kompatibilní blok, nastane jedna ze tří akcí:  
  
- Pokud je výjimka v finalizační metodě, finalizační metoda je přerušena a základní finalizační metoda, pokud existuje, je volána.  
  
- Pokud zásobník volání obsahuje statický konstruktor nebo inicializátor statických polí, <xref:System.TypeInitializationException> je vyvolána, s původní výjimkou přiřazenou <xref:System.Exception.InnerException%2A> vlastnosti nové výjimky.  
  
- Pokud je dosaženo začátku vlákna, vlákno je ukončeno.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Výjimky a jejich zpracování](./index.md)
