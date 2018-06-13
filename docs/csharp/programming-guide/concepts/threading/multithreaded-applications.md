---
title: Vícevláknové aplikace (C#)
ms.date: 07/20/2015
ms.assetid: b7015cfb-d506-4eac-b2f8-b2caaa9cc977
ms.openlocfilehash: ee4d92ae0ad3dadf6568b367522817484cb7337f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336040"
---
# <a name="multithreaded-applications-c"></a>Vícevláknové aplikace (C#)
Díky C# můžete vytvořit aplikace, které provádějí více úkolů ve stejnou dobu. Úlohy s potenciálně pojme dalších úloh můžete provést v samostatných vláknech, tento proces se označuje jako *multithreading* nebo *volné dělení na vlákna*.  
  
 Aplikace, které jsou rychlejší reakce na uživatelský vstup, protože uživatelské rozhraní zůstane aktivní, jak je náročná na výkon procesoru úkoly spustí v samostatných vláknech používání více vláken. Multithreading je také užitečné, když vytvoříte škálovatelné aplikace, protože vláken můžete přidat jako zvyšuje zatížení.  
  
## <a name="creating-and-using-threads"></a>Vytváření a používání vláken  
 Pokud potřebujete větší kontrolu nad chováním aplikace vláken, můžete spravovat vláken sami. Ale potřeba si uvědomit, zápis správné vícevláknové aplikace může být složité: vaše aplikace může přestat reagovat nebo dojde k přechodné chybě způsobené časování. Další informace najdete v tématu [vláken komponent](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).  
  
 Vytvořit nové vlákno deklarováním proměnné typu <xref:System.Threading.Thread> a volání konstruktoru, poskytuje název postupu nebo metodu, kterou chcete provést na nové vlákno. Následující kód představuje příklad.  
  
```csharp  
System.Threading.Thread newThread =  
    new System.Threading.Thread(AMethod);  
```  
  
### <a name="starting-and-stopping-threads"></a>Spouštění a zastavování vláken  
 Chcete-li spustit provádění nové vlákno, použijte <xref:System.Threading.Thread.Start%2A> metoda, jak je znázorněno v následujícím kódu.  
  
```csharp  
newThread.Start();  
```  
  
 Chcete-li zastavit provádění vlákna, použijte <xref:System.Threading.Thread.Abort%2A> metoda, jak je znázorněno v následujícím kódu.  
  
```csharp  
newThread.Abort();  
```  
  
 Kromě toho, spouštění a zastavování vláken, je také možné pozastavit vláken voláním <xref:System.Threading.Thread.Sleep%2A> nebo <xref:System.Threading.Thread.Suspend%2A> metoda, obnovit pozastavenou vlákno pomocí <xref:System.Threading.Thread.Resume%2A> metoda a zrušení vlákno pomocí <xref:System.Threading.Thread.Abort%2A> – metoda  
  
### <a name="thread-methods"></a>Metody přístup z více vláken  
 V následující tabulce jsou uvedeny některé metody, které můžete použít k řízení jednotlivých vláken.  
  
|Metoda|Akce|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A>|Způsobí, že vlákno k spustí.|  
|<xref:System.Threading.Thread.Sleep%2A>|Vlákna pozastaví po určitou dobu.|  
|<xref:System.Threading.Thread.Suspend%2A>|Vlákna pozastaví při dosažení bod bezpečné.|  
|<xref:System.Threading.Thread.Abort%2A>|Vlákno zastaví, když dorazí do bod bezpečné.|  
|<xref:System.Threading.Thread.Resume%2A>|Restartuje pozastavenou vlákna|  
|<xref:System.Threading.Thread.Join%2A>|Způsobí, že aktuální vlákno čekat na dokončení jiné vlákno. Pokud se používá s hodnotu časového limitu, vrátí tato metoda `True` Pokud skončí vlákno v přiděleném čase.|  
  
### <a name="safe-points"></a>Bezpečné body  
 Většina těchto metod jsou samovysvětlující, ale koncept *bezpečné body* může být pro vás nový. Bezpečné body jsou umístění v kódu, kde je bezpečný pro modul common language runtime provést automatické *uvolňování paměti*, proces uvolňování nepoužívané proměnné a opětovného získání paměti. Při volání <xref:System.Threading.Thread.Abort%2A> nebo <xref:System.Threading.Thread.Suspend%2A> metoda vlákno, modul common language runtime analyzuje kód a určuje umístění požadované místo pro vlákno zastavení.  
  
### <a name="thread-properties"></a>Vlastnosti vlákna  
 Vláken taky obsahovat užitečné několik vlastností, jak je znázorněno v následující tabulce:  
  
|Vlastnost|Hodnota|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Obsahuje hodnotu `True` Pokud vlákno je aktivní.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Získá nebo nastaví logickou hodnotu, která určuje, pokud je na vlákno, nebo by měly být vlákna na pozadí. Vlákna na pozadí jsou jako vlákna na popředí, ale vlákna na pozadí nezabrání proces zastavit. Jakmile je nutné zastavit všechna vlákna na popředí, které patří do procesu, modul common language runtime ukončí proces voláním <xref:System.Threading.Thread.Abort%2A> metodu vlákna na pozadí, které jsou stále aktivní.|  
|<xref:System.Threading.Thread.Name%2A>|Získá nebo nastaví název vlákna. Nejčastěji používá ke zjišťování jednotlivých vláken při ladění.|  
|<xref:System.Threading.Thread.Priority%2A>|Získá nebo nastaví hodnotu, která se používá v operačním systému k určení priority plánování přístup z více vláken.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Obsahuje hodnotu, která popisuje stavu nebo stavy, které vlákno.|  
  
## <a name="thread-priorities"></a>Priority přístup z více vláken  
 Každé vlákno má vlastnost priority, která určuje, jak velký či malý řez času procesoru je provést. Operační systém přiděluje delší časové úseky, můžete s vysokou prioritou vlákna a kratší časových řezů na nízkou prioritu vláken. Nové vláken jsou vytvořené s hodnotou `Normal`, ale můžete změnit <xref:System.Threading.Thread.Priority%2A> vlastnost na jakoukoli hodnotu v <xref:System.Threading.ThreadPriority> výčtu.  
  
 V tématu <xref:System.Threading.ThreadPriority> podrobný popis různých priorit přístup z více vláken.  
  
## <a name="foreground-and-background-threads"></a>Vlákna v popředí a v pozadí  
 A *vlákna na popředí* spustí po neomezenou dobu, zatímco *vlákna na pozadí* zastaví, jakmile poslední vlákno popředí byla zastavena. Můžete použít <xref:System.Threading.Thread.IsBackground%2A> vlastnosti k určení, nebo změňte stav vlákna na pozadí.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Thread>  
 [Synchronizace vláken (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [Parametry a návratové hodnoty pro procedury ve více vláknech (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)  
 [Dělení na vlákna (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)
