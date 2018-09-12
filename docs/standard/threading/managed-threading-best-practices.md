---
title: Doporučené postupy spravovaného dělení na vlákna
ms.date: 11/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f95fb3ccab7362021a7a195ea199a1370e003dd2
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44508592"
---
# <a name="managed-threading-best-practices"></a>Doporučené postupy spravovaného dělení na vlákna
Multithreading vyžaduje pečlivé programování. V případě většiny úkolů lze omezit složitost umístěním požadavků do fronty pro spuštění pomocí vláken fondu vláken. Toto téma řeší obtížnější situace, například koordinaci práce více vláken nebo zpracování vláken, která se blokují.  
  
> [!NOTE]
> Od verze rozhraní .NET Framework 4, Task Parallel Library a PLINQ poskytuje rozhraní API, která snižuje do hry složitost a rizika vícevláknového programování. Další informace najdete v tématu [paralelní programování v .NET](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="deadlocks-and-race-conditions"></a>Zablokování a konflikty časování  
 Multithreading řeší problémy s propustností a rychlostí odezvy, ale zároveň přináší nové problémy: zablokování a konflikty časování.  
  
### <a name="deadlocks"></a>Zablokování  
 K zablokování dochází tehdy, pokud se každé ze dvou vláken pokusí uzamknout prostředek, který je již zamčený. Ani jedno vlákno nemůže provádět žádný další krok.  
  
 Mnoho metod tříd modelu spravovaných vláken poskytuje časové limity, které usnadňují zjišťování případů zablokování. Například následující kód pokouší získat zámek na objekt s názvem `lockObject`. Pokud nezíská zámek do 300 milisekund, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> vrátí `false`.  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a>Konflikty časování  
 Konflikt časování je chyba, ke které dojde, pokud výstup programu závisí na tom, které ze dvou nebo více vláken dříve dosáhne určitého bloku kódu. Opakované spuštění programu vrací různé výsledky a nelze předpovědět výsledek jakéhokoli daného běhu.  
  
 Jednoduchým příkladem konfliktu časování je zvyšování pole. Předpokládejme, že třída má privátní **statické** pole (**Shared** v jazyce Visual Basic), které se navyšuje pokaždé, když je vytvořena instance třídy pomocí kódu, jako `objCt++;` (C#) nebo `objCt += 1` () Visual Basic). Tato operace vyžaduje načtení hodnoty z kódu `objCt` do registru, navýšení hodnoty a její uložení v kódu `objCt`.  
  
 Ve vícevláknových aplikacích platí, že vlákno, které načetlo a zvýšilo hodnotu, může být přerušeno jiným vláknem, jež provede všechny tři kroky. Pokud první vlákno pokračuje v provádění a uloží svou hodnotu, přepíše kód `objCt`, aniž by zohlednilo, že hodnota se mezitím změnila.  
  
 Těmto konkrétním konfliktům časování se dá snadno vyhnout použitím metod třídy <xref:System.Threading.Interlocked>, jako například <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>. Další informace o jiných technikách pro synchronizaci dat mezi více vláken, naleznete v tématu [synchronizace dat pro Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).  
  
 Ke konfliktům časování může docházet také tehdy, pokud synchronizujete aktivity více vláken. Při každém zápisu řádku kódu je nutné zvážit, co může nastat, pokud by vlákno bylo před provedením daného řádku (nebo před provedením jakéhokoliv jednotlivého pokynu počítače, který řádek tvoří) přerušeno a jiné vlákno by jej nahradilo.  
  
## <a name="number-of-processors"></a>Počet procesorů  
 Většina počítačů dnes již obsahuje více procesorů (také nazývané jádra), dokonce i v malých zařízeních, jako jsou tablety a telefony. Víte-li, že vyvíjíte software, který bude spouštěn také na jednoprocesorových počítačích, je zapotřebí si uvědomit, že multithreading řeší odlišné problémy pro jednoprocesorové a víceprocesorové počítače.  
  
### <a name="multiprocessor-computers"></a>Počítače s více procesory  
 Multithreading poskytuje větší propustnost. Deset procesorů může provést desetkrát více práce než jeden procesor, ale pouze pokud je práce rozdělena tak, aby všech deset procesorů mohlo pracovat současně. Vlákna poskytují snadný způsob rozdělení práce a využití tohoto vysokého výkonu. Pokud používáte multithreading na počítači s více procesory:  
  
-   Počet vláken, která mohou být prováděna současně, je omezen počtem procesorů.  
  
-   Vlákno na pozadí se provádí pouze v případě, že počet vláken v popředí je menší než počet procesorů.  
  
-   Pokud voláte metodu <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> na vlákno, pak dané vlákno může, ale nemusí, okamžitě spustit provádění, a to v závislosti na počtu procesorů a počtu vláken, která čekají na provedení.  
  
-   Ke konfliktům časování nemusí dojít pouze v případě, že jsou vlákna neočekávaně přerušena, ale i v situaci, kdy jsou prováděna dvě vlákna na různých procesorech a soupeří o dosažení stejného bloku kódu.  
  
### <a name="single-processor-computers"></a>Počítače s jedním procesorem  
 Multithreading poskytuje větší rychlost odezvy na činnost uživatele a pro úkoly na pozadí využívá čas nečinnosti. Pokud používáte multithreading na počítači s jedním procesorem:  
  
-   V jednom okamžiku se provádí pouze jedno vlákno.  
  
-   Vlákno na pozadí se spustí pouze tehdy, pokud je nečinné hlavní uživatelské vlákno. Vlákno na popředí, které se provádí nepřetržitě, ubírá vláknům na pozadí čas procesoru.  
  
-   Pokud voláte metodu <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> na vlákno, pak se dané vlákno nespustí, dokud se provádí aktuální vlákno nebo dokud není přerušeno operačním systémem.  
  
-   Ke konfliktům časování obvykle dochází tehdy, pokud programátor nepředpokládal skutečnost, že vlákno může být přerušeno v nevhodnou chvíli, což někdy umožní jinému vláknu dosáhnout určitého bloku kódu jako první.  
  
## <a name="static-members-and-static-constructors"></a>Statické členy a statické konstruktory  
 Třída není inicializována až do té doby, dokud příslušný konstruktor třídy (konstruktor `static` v jazyce C#, konstruktor `Shared Sub New` v jazyce Visual Basic) nedokončí provádění. Aby nedošlo ke spuštění kódu pro typ, který není inicializován, blokuje modul CLR všechna volání členů `static` dané třídy (`Shared` v jazyce Visual Basic) z jiných vláken až do dokončení konstruktoru třídy.  
  
 Pokud například konstruktor třídy začíná nové vlákno a procedura vlákna volá člen `static` dané třídy, je nové vlákno blokováno do doby, než je konstruktor třídy dokončen.  
  
 To platí pro jakýkoli typ, který může mít konstruktor `static`.  
  
## <a name="general-recommendations"></a>Obecná doporučení  
 Při používání více vláken zvažte následující pokyny:  
  
-   Pro ukončení ostatních vláken nepoužívejte vlákno <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Volání **přerušit** na jiné vlákno se podobá vyvolání výjimky na, že vlákno, bez znalosti, jakého bodu vlákno bylo dosaženo zpracovávání dosáhlo.  
  
-   Pro synchronizaci činností více vláken nepoužívejte vlákna <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>. Použijte vlákna <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent> a <xref:System.Threading.Monitor>.  
  
-   Řízení zpracovávání pracovních vláken neprovádějte z hlavního programu (například pomocí událostí). Namísto toho je vhodné navrhnout program tak, aby pracovní vlákna byla zodpovědná za čekání, dokud není k dispozici činnost, kterou pak vykonají a oznámí ostatním částem programu, že byla dokončena. Pokud nejsou pracovní vlákna blokovací, zvažte používání vláken fondu vláken. Volání metody <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> je užitečné v situacích, kdy pracovní vlákna provádí blokování.  
  
-   Nepoužívejte typy jako objekty zámku. To znamená, že byste neměli používat kódy, jako je `lock(typeof(X))` v jazyce C# nebo `SyncLock(GetType(X))` v jazyce Visual Basic, nebo používat kód <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> s objekty <xref:System.Type>. Pro daný typ existuje pouze jedna instance <xref:System.Type?displayProperty=nameWithType> v doméně aplikace. V případě, že typ, pro který použijete zámek, je veřejný, může jej jiný kód uzamknout, což povede k zablokování. Další informace najdete v části [spolehlivost – doporučené postupy](../../../docs/framework/performance/reliability-best-practices.md).  
  
-   Při zamykání instancí, například `lock(this)` v jazyce C# nebo `SyncLock(Me)` v jazyce Visual Basic, buďte obezřetní. Pokud jiný kód v aplikaci, který je vůči typu externí, převezme zámek objektu, může dojít k zablokování.  
  
-   Zajistěte, aby vlákno, které se zobrazilo v monitorovacím nástroji, jej opustilo vždy, i pokud dojde k výjimce během zobrazení vlákna v monitorovacím nástroji. C# [Zámek](~/docs/csharp/language-reference/keywords/lock-statement.md) příkazu a Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) příkaz zajišťují toto chování automaticky, když **nakonec** blok k Ujistěte se, že <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> je volá se. Pokud nelze zajistit, aby **ukončovací** bude volána, zvažte změnu návrhu a použít **Mutex**. Objekt mutex je automaticky uvolněn, pokud se ukončí vlákno, které jej vlastní.  
  
-   Pro úkoly, jež vyžadují různé prostředky, používejte více vláken a zamezte přiřazení většího počtu vláken jedinému prostředku. Například všechny úkoly zahrnující vstup-výstup těží z toho, že mají vlastní vlákno, protože dané vlákno bude přerušováno během vstupně-výstupních operací, a tím umožní provedení jiných vláken. Uživatelský vstup je dalším prostředkem, který těží z vyhrazeného vlákna. Úkol, který vyžaduje intenzivní výpočty, existuje na počítači s jedním procesorem spolu s uživatelským vstupem a s úkoly, jež se týkají vstupu-výstupu, ale úkoly s vícenásobnými intenzivními výpočty si vzájemně konkurují.  
  
-   Pro jednoduché změny stavu je třeba zvážit použití metod třídy <xref:System.Threading.Interlocked> namísto používání příkazu `lock` (`SyncLock` v jazyce Visual Basic). Příkaz `lock` je dobrý univerzální nástroj, avšak třída <xref:System.Threading.Interlocked> poskytuje lepší výkon aktualizací, které musí být atomické. Pokud neexistují žádné kolize, provede interně jedinou předponu zámku. V revizích kódu hledejte stejný kód, jaký je uveden v následujících příkladech. V prvním příkladu je zvýšena stavová proměnná:  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)   
    {  
        myField++;  
    }  
    ```  
  
     Pokud použijete metodu <xref:System.Threading.Interlocked.Increment%2A> namísto příkazu `lock`, můžete zlepšit výkon, a to následovně:  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  V rozhraní .NET Framework verze 2.0 poskytuje metoda <xref:System.Threading.Interlocked.Add%2A> atomické aktualizace v přírůstcích větších než 1.  
  
     Ve druhém příkladu je proměnná referenčního typu aktualizována pouze tehdy, pokud má odkaz hodnotu null (`Nothing` v jazyce Visual Basic).  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     Výkon lze zvýšit pomocí metody <xref:System.Threading.Interlocked.CompareExchange%2A>, jak je zobrazeno dále:  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  V rozhraní .NET Framework verze 2.0 má metoda <xref:System.Threading.Interlocked.CompareExchange%2A> obecné přetížení, které může být použito pro typově bezpečné nahrazení jakéhokoliv odkazového typu.  
  
## <a name="recommendations-for-class-libraries"></a>Doporučení pro knihovny tříd  
 Při navrhování knihoven tříd pro multithreading zvažte následující pokyny:  
  
-   Pokud je to možné, synchronizaci nepoužívejte. To zejména platí pro velmi vytížený kód. Algoritmus může být například upraven pro tolerování konfliktů časování spíše než pro jejich odstranění. Zbytečná synchronizace snižuje výkon a vytvoří možnosti pro zablokování a konflikty časování.  
  
-   Zajistěte, aby data deklarovaná jako static (`Shared` v jazyce Visual Basic) byla ve výchozím nastavení bezpečná pro přístup z více vláken.  
  
-   Nenastavujte data instancí ve výchozím nastavení jako bezpečná pro přístup z více vláken. Přidávání zámků za účelem vytvoření kódu bezpečného pro přístup z více vláken snižuje výkon, zvyšuje kolize zámků a vytváří možnost zablokování. V běžných modelech aplikací provádí uživatelský kód v každém okamžiku pouze jedno vlákno, což minimalizuje potřebu zabezpečení pro přístup z více vláken. Z tohoto důvodu nejsou knihovny tříd rozhraní .NET Framework ve výchozím nastavení bezpečné pro přístup z více vláken.  
  
-   Nepoužívejte poskytování statických metod, které mění stav. V případě běžných použití serverů je statický stav sdílen napříč požadavky, což znamená, že více vláken může současně spustit tento kód. Tato skutečnost otevírá možnosti pro chyby spojené s používáním více vláken. Zvažte používání návrhového vzoru, který zapouzdřuje data do instancí, jež nejsou sdíleny napříč požadavky. Dále platí, že pokud jsou synchronizována statická data, volání mezi statickými metodami, které mění stav, může způsobit zablokování nebo redundantní synchronizaci, což nepříznivě ovlivňuje výkon.  
  
## <a name="see-also"></a>Viz také:

- [Dělení na vlákna](../../../docs/standard/threading/index.md)  
- [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)
