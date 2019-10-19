---
title: Příkaz SyncLock (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: e981ee727b66ecda392014fd3ee8ca6f1526cd2e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578902"
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
 Požadováno. Výraz, který se vyhodnocuje jako odkaz na objekt.  
  
 `block`  
 Volitelné. Blok příkazů, které mají být provedeny při získání zámku.  
  
 `End SyncLock`  
 Ukončí blok `SyncLock`.  
  
## <a name="remarks"></a>Poznámky  
 Příkaz `SyncLock` zajišťuje, že více vláken nespustí blok příkazu současně. `SyncLock` zabrání každému vláknu v vstupu do bloku, dokud žádné jiné vlákno neprovádí.  
  
 Nejběžnějším použitím `SyncLock` je chránit data před jejich aktualizací více než jedním vláknem současně. Pokud příkazy, které pracují s daty, musí přejít k dokončení bez přerušení, umístit je do bloku `SyncLock`.  
  
 Blok příkazu chráněný výhradním zámkem se někdy nazývá *kritická sekce*.  
  
## <a name="rules"></a>Pravidly  
  
- Větvení. Nemůžete vytvořit větev `SyncLock` bloku z vnějšího bloku.  
  
- Zamkne hodnotu objektu. Hodnotu `lockobject` nelze `Nothing`. Objekt zámku je nutné vytvořit před jeho použitím v příkazu `SyncLock`.  
  
     Při provádění bloku `SyncLock` nemůžete změnit hodnotu `lockobject`. Mechanismus vyžaduje, aby objekt zámku zůstal beze změny.  
  
- V bloku `SyncLock` nemůžete použít operátor [await](../../../visual-basic/language-reference/operators/await-operator.md) .  
  
## <a name="behavior"></a>Předvídatelně  
  
- Mechanismy. Když vlákno dosáhne příkazu `SyncLock`, vyhodnotí výraz `lockobject` a pozastaví provádění, dokud nezíská výhradní zámek objektu vráceného výrazem. Když další vlákno dosáhne příkazu `SyncLock`, nezíská zámek, dokud první vlákno nespustí příkaz `End SyncLock`.  
  
- Chráněná data. Pokud je `lockobject` `Shared` proměnné, exkluzivní zámek zabraňuje vláknu v jakékoli instanci třídy ve spuštění bloku `SyncLock`, zatímco jakékoli jiné vlákno provádí jeho spuštění. Tato ochrana chrání data, která jsou sdílena mezi všemi instancemi.  
  
     Pokud `lockobject` je proměnná instance (není `Shared`), zámek brání vláknu běžícímu v aktuální instanci ve stejném okamžiku, kdy je spuštěn blok `SyncLock` ve stejnou dobu jako jiné vlákno ve stejné instanci. Tato ochrana chrání data udržovaná individuální instancí.  
  
- Získání a vydání. @No__t_0 blok se chová jako `Try...Finally` konstrukce, ve které blok `Try` získá výhradní zámek na `lockobject` a `Finally` blok ho uvolní. Z tohoto důvodu blok `SyncLock` garantuje vydání zámku bez ohledu na to, jak tento blok ukončujete. To platí i v případě neošetřené výjimky.  
  
- Volání rozhraní. Blok `SyncLock` získá a uvolní výhradní zámek voláním metod `Enter` a `Exit` třídy `Monitor` v oboru názvů <xref:System.Threading>.  
  
## <a name="programming-practices"></a>Postupy programování  
 Výraz `lockobject` by měl vždy vyhodnocovat objekt, který patří výhradně do vaší třídy. Měli byste deklarovat `Private` proměnnou objektu, chcete-li chránit data, která patří do aktuální instance, nebo proměnnou objektu `Private Shared` a chránit tak data společná pro všechny instance.  
  
 Klíčové slovo `Me` byste neměli používat k poskytnutí objektu zámku pro data instance. Pokud má externí kód pro vaši třídu odkaz na instanci vaší třídy, může použít tento odkaz jako objekt zámku pro `SyncLock` blok, který zcela odlišná od vaší ze svých vlastních dat. Tímto způsobem může vaše třída a druhá třída vzájemně blokovat provádění jejich nesouvisejících `SyncLock`ch bloků. Podobně zamykání na řetězci může být problematické, protože jakýkoliv jiný kód v procesu používající stejný řetězec bude sdílet stejný zámek.  
  
 Kromě toho byste neměli používat metodu `Me.GetType` k poskytnutí objektu zámku pro sdílená data. Důvodem je, že `GetType` vždy vrací stejný objekt `Type` pro daný název třídy. Externí kód může volat `GetType` ve vaší třídě a získat stejný objekt zámku, který používáte. To by vedlo k tomu, že obě třídy jsou vzájemně blokující od jejich `SyncLock`ch bloků.  
  
## <a name="examples"></a>Příklady  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje třídu, která udržuje jednoduchý seznam zpráv. Obsahuje zprávy v poli a posledním použitém elementu tohoto pole v proměnné. @No__t_0 procedura zvýší poslední prvek a uloží novou zprávu. Tyto dvě operace jsou chráněny pomocí příkazů `SyncLock` a `End SyncLock`, protože po zvýšení posledního prvku musí být nová zpráva uložena předtím, než jakékoli jiné vlákno bude moci znovu zvýšit poslední prvek.  
  
 Pokud `simpleMessageList` třída sdílela jeden seznam zpráv mezi všemi jeho instancemi, proměnné `messagesList` a `messagesLast` budou deklarovány jako `Shared`. V takovém případě by měla být proměnná `messagesLock` také `Shared`, takže by existoval jeden objekt zámku používaný každou instancí.  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>Popis  
 Následující příklad používá vlákna a `SyncLock`. Pokud je přítomen příkaz `SyncLock`, je blok příkazu kritickým oddílem a `balance` nikdy se nestane záporným číslem. Můžete přidat komentář k příkazům `SyncLock` a `End SyncLock` a zobrazit efekt vynechání klíčového slova `SyncLock`.  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>Komentáře  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Přehled primitiv synchronizace](../../../standard/threading/overview-of-synchronization-primitives.md)
