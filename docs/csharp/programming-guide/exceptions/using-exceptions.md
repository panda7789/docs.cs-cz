---
title: Použití výjimek – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 4012027dc1a9bd2543d0a4195360e5f7e0586fe1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705259"
---
# <a name="using-exceptions-c-programming-guide"></a>Použití výjimek (Průvodce programováním v C#)
V C#systému jsou chyby v programu v době běhu šířeny prostřednictvím programu pomocí mechanismu nazývaného výjimky. Výjimky jsou vyvolány kódem, který zaznamená chybu a zachycena kódem, který může chybu opravit. Výjimky mohou být vyvolány .NET Framework Common Language Runtime (CLR) nebo pomocí kódu v programu. Jakmile je vyvolána výjimka, rozšíří zásobník volání, dokud není nalezen příkaz `catch` pro výjimku. Nezachycené výjimky jsou zpracovávány pomocí obecné obslužné rutiny výjimky poskytované systémem, který zobrazuje dialogové okno.  
  
 Výjimky jsou reprezentovány třídami odvozenými z <xref:System.Exception>. Tato třída identifikuje typ výjimky a obsahuje vlastnosti, které obsahují podrobnosti o výjimce. Vyvolání výjimky zahrnuje vytvoření instance třídy odvozené od výjimky, volitelně konfiguraci vlastností výjimky a následnou vyvolání objektu pomocí klíčového slova `throw`. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Po vyvolání výjimky modul runtime zkontroluje aktuální příkaz a zjistí, zda je v rámci `try`ho bloku. Pokud je, jsou zkontrolovány všechny `catch` bloky přidružené k bloku `try`, aby bylo vidět, zda mohou zachytit výjimku. bloky `Catch` obvykle určují typy výjimek; Pokud typ `catch` bloku je stejného typu jako výjimka nebo základní třída výjimky, může blok `catch` zpracovat metodu. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Pokud příkaz, který vyvolá výjimku, není v rámci `try` bloku nebo pokud blok `try`, který ho obklopuje, nemá odpovídající blok `catch`, modul runtime zkontroluje volající metodu pro příkaz `try` a `catch` bloky. Modul runtime pokračuje v zásobníku volání a hledá kompatibilní blok `catch`. Po nalezení a spuštění bloku `catch` je ovládací prvek předán dalšímu příkazu po tomto bloku `catch`.  
  
 Příkaz `try` může obsahovat více než jeden `catch` blok. První příkaz `catch`, který může zpracovat výjimku, je proveden; všechny následující příkazy `catch`, i když jsou kompatibilní, se ignorují. Proto by bloky catch měly být vždy řazeny z nejvíce specifického (nebo nejvíce odvozeného) na nejméně konkrétní. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 Před spuštěním bloku `catch` modul runtime vyhledá bloky `finally`. `Finally` bloky umožňují programátorovi vyčistit jakýkoli nejednoznačný stav, který by mohl zůstat z přerušeného `try` bloku, nebo uvolnit jakékoli externí prostředky (například grafické popisovače, databázová připojení nebo datové proudy souborů) bez čekání na uvolnění paměti systémem uvolňování paměti v modulu runtime. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 Pokud `WriteByte()` vyvolala výjimku, kód v druhém bloku `try`, který se pokusí znovu otevřít soubor, by nebyl úspěšný, pokud `file.Close()` není volán a soubor by zůstal uzamčen. Vzhledem k tomu, že `finally` bloky jsou spouštěny i v případě, že dojde k výjimce, bloku `finally` v předchozím příkladu umožní, aby se soubor správně zavřel a pomáhá se vyhnout chybě.  
  
 Pokud v zásobníku volání není po vyvolání výjimky nalezen žádný kompatibilní blok `catch`, dojde k jedné ze tří akcí:  
  
- Pokud je výjimka v finalizační metodě, finalizační metoda je přerušena a základní finalizační metoda, pokud existuje, je volána.  
  
- Pokud zásobník volání obsahuje statický konstruktor nebo inicializátor statických polí, je vyvolána <xref:System.TypeInitializationException>, s původní výjimkou přiřazenou vlastnosti <xref:System.Exception.InnerException%2A> nové výjimky.  
  
- Pokud je dosaženo začátku vlákna, vlákno je ukončeno.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Výjimky a jejich zpracování](./index.md)
