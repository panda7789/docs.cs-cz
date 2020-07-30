---
title: Použití výjimek – Průvodce programováním v C#
description: Naučte se používat výjimky. Výjimky jsou vyvolány kódem, který zaznamená chybu a zachycena kódem, který chybu opraví.
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: fb45381f1c6cfa2f27d036ead8e662b7a0d8d924
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303371"
---
# <a name="use-exceptions-c-programming-guide"></a>Použití výjimek (Průvodce programováním v C#)

V jazyce C# jsou chyby v programu za běhu šířeny přes program pomocí mechanismu nazývaného výjimky. Výjimky jsou vyvolány kódem, který zaznamená chybu a zachycena kódem, který může chybu opravit. Výjimky mohou být vyvolány modulem runtime .NET nebo kódem v programu. Jakmile je vyvolána výjimka, rozšíří zásobník volání, dokud nebude `catch` nalezen příkaz pro výjimku. Nezachycené výjimky jsou zpracovávány pomocí obecné obslužné rutiny výjimky poskytované systémem, který zobrazuje dialogové okno.  
  
 Výjimky jsou reprezentovány třídami odvozenými z <xref:System.Exception> . Tato třída identifikuje typ výjimky a obsahuje vlastnosti, které obsahují podrobnosti o výjimce. Vyvolání výjimky zahrnuje vytvoření instance třídy odvozené od výjimky, volitelně konfiguraci vlastností výjimky a následné vyvolání objektu pomocí `throw` klíčového slova. Například:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Po vyvolání výjimky modul runtime zkontroluje aktuální příkaz a zjistí, zda je v rámci `try` bloku. Pokud je, `catch` jsou zkontrolovány všechny bloky přidružené k `try` bloku, aby bylo vidět, zda mohou zachytit výjimku. `Catch`bloky obvykle určují typy výjimek; Pokud `catch` je typ bloku shodný s typem výjimky nebo základní třídou výjimky, `catch` může blok zpracovat metodu. Například:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Pokud příkaz, který vyvolá výjimku, není uvnitř `try` bloku nebo pokud `try` blok, který ho obklopuje, nemá odpovídající `catch` blok, modul runtime zkontroluje volající metodu pro `try` příkaz a `catch` bloky. Modul runtime pokračuje v zásobníku volání a hledá kompatibilní `catch` blok. Po `catch` nalezení a provedení bloku je ovládací prvek předán dalšímu příkazu po tomto `catch` bloku.  
  
 `try`Příkaz může obsahovat více než jeden `catch` blok. `catch`Je proveden první příkaz, který může zpracovat výjimku; všechny následující `catch` příkazy, i když jsou kompatibilní, jsou ignorovány. Proto by bloky catch měly být vždy řazeny z nejvíce specifického (nebo nejvíce odvozeného) na nejméně konkrétní. Například:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 Před `catch` provedením bloku modul runtime vyhledá `finally` bloky. `Finally`bloky umožňují programátorovi vyčistit libovolný nejednoznačný stav, který by mohl zůstat z přerušeného `try` bloku, nebo uvolnit externí prostředky (jako jsou grafické popisovače, databázová připojení nebo datové proudy souborů), aniž by čekali, až uvolňování paměti v modulu runtime dokončí objekty. Například:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 Pokud `WriteByte()` vyvolal výjimku, kód v druhém `try` bloku, který se pokusí znovu otevřít soubor `file.Close()` , selže, pokud není volán, a soubor by zůstal uzamčen. Vzhledem k tomu `finally` , že jsou bloky spouštěny i v případě, že dojde k výjimce, `finally` blok v předchozím příkladu umožňuje, aby se soubor správně zavřel, a pomáhá vyhnout se chybě.  
  
 Pokud `catch` v zásobníku volání není po vyvolání výjimky nalezen žádný kompatibilní blok, nastane jedna ze tří akcí:  
  
- Pokud je výjimka v finalizační metodě, finalizační metoda je přerušena a základní finalizační metoda, pokud existuje, je volána.  
  
- Pokud zásobník volání obsahuje statický konstruktor nebo inicializátor statických polí, <xref:System.TypeInitializationException> je vyvolána, s původní výjimkou přiřazenou <xref:System.Exception.InnerException%2A> Vlastnosti nové výjimky.  
  
- Pokud je dosaženo začátku vlákna, vlákno je ukončeno.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Výjimky a zpracování výjimek](./index.md)
