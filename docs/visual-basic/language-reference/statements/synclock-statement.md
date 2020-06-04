---
title: SyncLock – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: fd932a20af274faf2b56136a94675b28399989b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404158"
---
# <a name="synclock-statement"></a>SyncLock – příkaz
Získá výhradní zámek pro blok příkazu před spuštěním bloku.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Součásti  
 `lockobject`  
 Povinná hodnota. Výraz, který se vyhodnocuje jako odkaz na objekt.  
  
 `block`  
 Nepovinný parametr. Blok příkazů, které mají být provedeny při získání zámku.  
  
 `End SyncLock`  
 Ukončí `SyncLock` blok.  
  
## <a name="remarks"></a>Poznámky  
 `SyncLock`Příkaz zajistí, že více vláken nespustí blok příkazu současně. `SyncLock`zabrání každému vláknu v vstupu do bloku, dokud žádné jiné vlákno neprovádí.  
  
 Nejběžnějším použitím nástroje `SyncLock` je chránit data před aktualizací více než jedním vláknem současně. Pokud příkazy, které pracují s daty, musí přejít k dokončení bez přerušení, umístit je dovnitř `SyncLock` bloku.  
  
 Blok příkazu chráněný výhradním zámkem se někdy nazývá *kritická sekce*.  
  
## <a name="rules"></a>Pravidla  
  
- Větvení. Nemůžete vytvořit větev do `SyncLock` bloku z vnějšího bloku.  
  
- Zamkne hodnotu objektu. Hodnota `lockobject` nemůže být `Nothing` . Objekt zámku je nutné vytvořit před jeho použitím v `SyncLock` příkazu.  
  
     Při provádění bloku nelze změnit hodnotu `lockobject` `SyncLock` . Mechanismus vyžaduje, aby objekt zámku zůstal beze změny.  
  
- V bloku nelze použít operátor [await](../operators/await-operator.md) `SyncLock` .  
  
## <a name="behavior"></a>Chování  
  
- Mechanismy. Když vlákno dosáhne `SyncLock` příkazu, vyhodnotí `lockobject` výraz a pozastaví provádění, dokud nezíská výhradní zámek objektu vráceného výrazem. Když jiný podproces dosáhne `SyncLock` příkazu, nezíská zámek, dokud první vlákno neprovede `End SyncLock` příkaz.  
  
- Chráněná data. Pokud `lockobject` je `Shared` Proměnná, exkluzivní zámek zabraňuje vláknu v jakékoli instanci třídy, aby vyspustila blok, `SyncLock` zatímco jakékoli jiné vlákno ji provádí. Tato ochrana chrání data, která jsou sdílena mezi všemi instancemi.  
  
     Pokud `lockobject` je proměnná instance (ne `Shared` ), zámek zabraňuje vláknu běžícímu v aktuální instanci spouštět `SyncLock` blok ve stejnou dobu jako jiné vlákno ve stejné instanci. Tato ochrana chrání data udržovaná individuální instancí.  
  
- Získání a vydání. `SyncLock`Blok se chová jako `Try...Finally` konstrukce, ve které `Try` blok získá výhradní zámek `lockobject` , a `Finally` blok ho uvolní. Z tohoto důvodu `SyncLock` blok garantuje vydání zámku bez ohledu na to, jak tento blok ukončujete. To platí i v případě neošetřené výjimky.  
  
- Volání rozhraní. `SyncLock`Blok získá a uvolní výhradní zámek voláním `Enter` `Exit` metod a `Monitor` třídy v <xref:System.Threading> oboru názvů.  
  
## <a name="programming-practices"></a>Postupy programování  
 `lockobject`Výraz by měl vždy vyhodnocovat objekt, který patří exkluzivně do vaší třídy. Měli byste deklarovat `Private` objektovou proměnnou pro ochranu dat patřících k aktuální instanci nebo `Private Shared` proměnné objektu pro ochranu dat společných pro všechny instance.  
  
 Klíčové slovo byste neměli používat `Me` k poskytnutí objektu zámku pro data instance. Pokud má externí kód pro vaši třídu odkaz na instanci vaší třídy, může použít tento odkaz jako objekt zámku pro `SyncLock` blok zcela odlišný od vašeho ze své ochrany a chránit tak jiná data. Tímto způsobem může vaše třída a druhá třída vzájemně blokovat spouštění jejich nesouvisejících `SyncLock` bloků. Podobně zamykání na řetězci může být problematické, protože jakýkoliv jiný kód v procesu používající stejný řetězec bude sdílet stejný zámek.  
  
 Tuto metodu byste neměli používat ani `Me.GetType` k poskytnutí objektu zámku pro sdílená data. Je to proto `GetType` , že vždy vrátí stejný `Type` objekt pro daný název třídy. Externí kód by mohl zavolat `GetType` na vaši třídu a získat stejný objekt zámku, který používáte. To by vedlo ke vzájemnému blokování obou tříd z jejich `SyncLock` bloků.  
  
## <a name="examples"></a>Příklady  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje třídu, která udržuje jednoduchý seznam zpráv. Obsahuje zprávy v poli a posledním použitém elementu tohoto pole v proměnné. `addAnotherMessage`Procedura zvýší poslední prvek a uloží novou zprávu. Tyto dvě operace jsou chráněny pomocí `SyncLock` `End SyncLock` příkazů a, protože po zvýšení posledního prvku se musí nová zpráva uložit předtím, než jakékoli jiné vlákno bude moci znovu zvýšit poslední prvek.  
  
 Pokud `simpleMessageList` Třída sdílela jeden seznam zpráv mezi všemi jeho instancemi, proměnné `messagesList` a by měly `messagesLast` být deklarovány jako `Shared` . V takovém případě `messagesLock` by měla být proměnná také `Shared` , takže by existoval jediný objekt zámku, který používá každá instance.  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>Description  
 Následující příklad používá vlákna a `SyncLock` . Pokud `SyncLock` je k dispozici příkaz, blok příkazu je nepostradatelným oddílem a `balance` nikdy se nestane záporným číslem. Můžete komentovat `SyncLock` příkazy a a podívat se, `End SyncLock` Jak `SyncLock` klíčové slovo opustí.  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>Komentáře  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Přehled primitiv synchronizace](../../../standard/threading/overview-of-synchronization-primitives.md)
