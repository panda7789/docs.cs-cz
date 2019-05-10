---
title: SyncLock – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: a2bd6ca11072113d8acff78032c19d48c30933c3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615130"
---
# <a name="synclock-statement"></a>SyncLock – příkaz
Získá výhradní zámek pro blok příkazů, který před spuštěním bloku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Součásti  
 `lockobject`  
 Povinný parametr. Výraz, který se vyhodnotí jako odkaz na objekt.  
  
 `block`  
 Volitelné. Blok příkazů, které se má provést, když je požadován zámek.  
  
 `End SyncLock`  
 Ukončí `SyncLock` bloku.  
  
## <a name="remarks"></a>Poznámky  
 `SyncLock` Prohlášení zajišťuje, že více vláken neprovádět tohoto bloku příkazů ve stejnou dobu. `SyncLock` každé vlákno zabrání v zadání bloku, dokud žádné vlákno provádí.  
  
 Nejběžnější použití nástroje `SyncLock` je k ochraně dat aktualizovány podle více než jedno vlákno současně. Pokud příkazy, které pracuje s daty musí přejít do dokončení bez přerušení, vytvořte z nich uvnitř `SyncLock` bloku.  
  
 Někdy se označuje jako blok příkazů, který je chráněn výhradní zámek *kritický oddíl*.  
  
## <a name="rules"></a>pravidla  
  
- Větvení. Nelze větvit do `SyncLock` znemožní mimo blok.  
  
- Hodnota objektu zámku. Hodnota `lockobject` nemůže být `Nothing`. Zamknout objekt musíte vytvořit předtím, než ho použijete `SyncLock` příkazu.  
  
     Nelze změnit hodnotu `lockobject` při provádění `SyncLock` bloku. Mechanismus vyžaduje, že zámek objektu zůstanou beze změny.  
  
- Nelze použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor `SyncLock` bloku.  
  
## <a name="behavior"></a>Chování  
  
- Mechanismus. Když vlákno dosáhne `SyncLock` prohlášení, vyhodnotí `lockobject` výraz a pozastaví spuštění, dokud získá výhradní zámek na objekt vrácený výrazem. Když jiné vlákno dosáhne `SyncLock` příkazu, to není získat zámek až do první vlákno spustí `End SyncLock` příkazu.  
  
- Chráněná Data. Pokud `lockobject` je `Shared` proměnné, vlákno v jakékoli instance třídy výhradní zámek brání v provádění `SyncLock` zablokuje při provádění jakékoli jiné vlákno. To chrání data, jež jsou sdílena mezi všemi instancemi.  
  
     Pokud `lockobject` je proměnná instance (ne `Shared`), zámek je chrání vlákna běžícího v aktuální instanci spuštění `SyncLock` bloku ve stejnou dobu jako jiné vlákno ve stejné instanci. To chrání data udržovaná jednotlivých instancí.  
  
- Získání a uvolnění. A `SyncLock` bloku se chová stejně jako `Try...Finally` konstrukce, ve kterém `Try` bloku získá výhradní zámek na `lockobject` a `Finally` ho uvolní blok. Z toho důvodu `SyncLock` bloku zaručuje uvolnění zámku, bez ohledu na to, jak ukončení bloku. To platí i v případě neošetřené výjimce.  
  
- Rámec volá. `SyncLock` Blokovat operace čtení a uvolní zámek voláním `Enter` a `Exit` metody `Monitor` třídy v <xref:System.Threading> oboru názvů.  
  
## <a name="programming-practices"></a>Postupy pro programování  
 `lockobject` Objekt, který patří do vaší třídy výhradně vždy by se měl vyhodnotit výraz. By měla deklarovat `Private` proměnné objektu k ochraně dat, které patří k aktuální instanci nebo `Private Shared` proměnné objektu k ochraně dat, které jsou společné pro všechny instance.  
  
 Neměli byste používat `Me` data pro instanci objektu – klíčové slovo kvůli zámku. Pokud má kód do vaší třídy externí odkaz na instanci třídy, pomocí tohoto odkazu jako objekt zámek pro `SyncLock` bloku zcela liší od patří vám, chrání různé datové. Tímto způsobem vaší třídy a jiná třída může blokovat mezi sebou z provádění jejich nesouvisejících `SyncLock` bloky. Podobně uzamčení na řetězec může být problematické, protože jakýkoli jiný kód v procesu pomocí stejný řetězec budou sdílet stejnou zámku.  
  
 Také byste neměli používat `Me.GetType` metodu k dispozici zámek objektu, pro sdílená data. Důvodem je, že `GetType` vždy vrátí stejné `Type` objekt pro název dané třídy. Externí kód lze zavolat `GetType` na třídě a získat stejné zamknout objekt, který používáte. To způsobí dvě třídy blokování druhý z jejich `SyncLock` bloky.  
  
## <a name="examples"></a>Příklady  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje třídu, která udržuje jednoduchý seznam zpráv. V poli obsahuje zprávy a poslední prvek pole použitá v proměnné. `addAnotherMessage` Postup zvýší poslední prvek a uloží novou zprávu. Tyto dvě operace jsou chráněny `SyncLock` a `End SyncLock` příkazy, protože po posledním prvku byl navýšen, nová zpráva musí být uložen před jakékoli vlákno může zvýšit poslední prvek znovu.  
  
 Pokud `simpleMessageList` třídy sdílí jeden seznam zpráv mezi všechny její instance, proměnné `messagesList` a `messagesLast` by být deklarovaný jako `Shared`. V tomto případě, proměnná `messagesLock` by mělo být také `Shared`, takže by existovat jeden zámek objekt použitý objektem každou instanci.  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>Popis  
 Následující příklad používá vlákna a `SyncLock`. Za předpokladu, `SyncLock` příkaz je k dispozici, je důležité části tohoto bloku příkazů a `balance` nikdy nebude záporné číslo. Můžete Zakomentovat `SyncLock` a `End SyncLock` příkazy a vidět její účinek ponechání navýšení kapacity `SyncLock` – klíčové slovo.  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>Komentáře  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Přehled primitiv synchronizace](../../../standard/threading/overview-of-synchronization-primitives.md)
