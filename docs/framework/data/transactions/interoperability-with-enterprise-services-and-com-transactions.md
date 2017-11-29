---
title: "Vzájemná funkční spolupráce s Enterprise služeb a transakcí modelu COM +"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0fd0d26-fe86-443b-b208-4d57d39fa4aa
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 14763de8861c06072f7f13928caa3327e9d7ff42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="interoperability-with-enterprise-services-and-com-transactions"></a>Vzájemná funkční spolupráce s Enterprise služeb a transakcí modelu COM +
<xref:System.Transactions> Obor názvů podporuje spolupráci mezi objekty transakce vytvořené pomocí tohoto oboru názvů a transakce vytvořené pomocí modelu COM +.  
  
 Můžete použít <xref:System.Transactions.EnterpriseServicesInteropOption> výčet při vytváření nového <xref:System.Transactions.TransactionScope> instance k zadání úrovně interoperability s modelu COM +.  
  
 Ve výchozím nastavení, pokud kód aplikace zkontroluje statických <xref:System.Transactions.Transaction.Current%2A> vlastnost <xref:System.Transactions> pokusí vyhledat transakci, která je jinak aktuální nebo <xref:System.Transactions.TransactionScope> objektu, která způsobila, že <xref:System.Transactions.Transaction.Current%2A> je **null**. Pokud tento soubor nelze nalézt jednu z těchto <xref:System.Transactions> dotazuje kontext modelu COM + pro transakci. Všimněte si, že i když <xref:System.Transactions> setkat s transakcí z modelu COM + kontextu, stále upřednostňuje transakcí, které jsou pro nativní <xref:System.Transactions>.  
  
## <a name="interoperability-levels"></a>Interoperabilita úrovně  
 <xref:System.Transactions.EnterpriseServicesInteropOption> Výčet definuje následující úrovně interoperability –<xref:System.Transactions.EnterpriseServicesInteropOption.None>, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> a <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>.  
  
 <xref:System.Transactions.TransactionScope> Třída poskytuje konstruktory, které přijímají <xref:System.Transactions.EnterpriseServicesInteropOption> jako parametr.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.None>, jak název naznačuje, znamená, že neexistuje žádná interoperability mezi <xref:System.EnterpriseServices> kontexty a obory transakce. Po vytvoření <xref:System.Transactions.TransactionScope> objekt s <xref:System.Transactions.EnterpriseServicesInteropOption.None>, veškeré změny <xref:System.Transactions.Transaction.Current%2A> se neprojeví v daném kontextu. Podobně změny transakce v rámci modelu COM + se neprojeví v <xref:System.Transactions.Transaction.Current%2A>. Jedná se o nejrychlejší režim operaci pro <xref:System.Transactions> vzhledem k tomu, že neexistuje žádná další synchronizace vyžadována. <xref:System.Transactions.EnterpriseServicesInteropOption.None>Výchozí hodnota používaná je <xref:System.Transactions.TransactionScope> s všechny konstruktory, které nepřijímá <xref:System.Transactions.EnterpriseServicesInteropOption> jako parametr.  
  
 Pokud chcete sloučit <xref:System.EnterpriseServices> transakce s okolí transakci, je nutné použít buď <xref:System.Transactions.EnterpriseServicesInteropOption.Full> nebo <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>. Oba tyto hodnoty jsou závislé na funkci služby bez součástí a proto vám by měl být spuštěn v systému Windows XP Service Pack 2 nebo Windows Server 2003 při jejich používání.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Full>Určuje, že okolí transakce pro <xref:System.Transactions> a <xref:System.EnterpriseServices> jsou vždy stejné. Je výsledkem vytvoření nového <xref:System.EnterpriseServices> transakční kontextu a transakcí, která byla platná pro použití <xref:System.Transactions.TransactionScope> je aktuální pro tento kontext. Jako takový transakce v <xref:System.Transactions.Transaction.Current%2A> je zcela synchronizaci s transakcí v <xref:System.EnterpriseServices.ContextUtil.Transaction%2A>. Tato hodnota představuje snížení výkonu vzhledem k tomu, že nový modelu COM + kontexty může být nutné k vytvoření.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>Určuje následující požadavky:  
  
-   Při <xref:System.Transactions.Transaction.Current%2A> je zaškrtnuto, <xref:System.Transactions> by měl podporu transakcí v rámci modelu COM +, jestliže zjistí, zda je spuštěna v kontextu jiných než výchozí kontext. Všimněte si, že výchozí kontext nemůže obsahovat transakcí. Proto ve výchozím kontextu, dokonce i s <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, transakce uložený v místním úložišti podprocesů používaný <xref:System.Transactions> je vrácena pro <xref:System.Transactions.Transaction.Current%2A>.  
  
-   Pokud nový <xref:System.Transactions.TransactionScope> objekt je vytvořen a dojde k vytvoření v jiném kontextu než výchozí kontext transakce, která je pro aktuální <xref:System.Transactions.TransactionScope> objekt by měl být projeví v modelu COM +. V takovém případě <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> se chová jako <xref:System.Transactions.EnterpriseServicesInteropOption.Full> v tom, vytvoří nový kontext modelu COM +.  
  
 Kromě toho při <xref:System.Transactions.Transaction.Current%2A> je nastavena v obou <xref:System.Transactions.EnterpriseServicesInteropOption.Full> a <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, obou těchto režimech znamenat, že <xref:System.Transactions.Transaction.Current%2A> nelze nastavit přímo.  Žádný pokus o nastavení <xref:System.Transactions.Transaction.Current%2A> přímo jiné než vytváření <xref:System.Transactions.TransactionScope> vede <xref:System.InvalidOperationException>. <xref:System.Transactions.EnterpriseServicesInteropOption> Hodnota výčtu zdědí nové obory transakce, které explicitně neurčí hodnotu, která se má použít. Například, pokud vytvoříte nový <xref:System.Transactions.TransactionScope> objekt s <xref:System.Transactions.EnterpriseServicesInteropOption.Full>a potom vytvořte druhý <xref:System.Transactions.TransactionScope> objektu, ale ne <xref:System.Transactions.EnterpriseServicesInteropOption> hodnotu, druhá <xref:System.Transactions.TransactionScope> objekt má také <xref:System.Transactions.EnterpriseServicesInteropOption.Full>.  
  
 V souhrnu při vytváření nového oboru transakce platí následující pravidla:  
  
1.  <xref:System.Transactions.Transaction.Current%2A>Chcete-li zjistit, zda je transakce je zaškrtnuto. Výsledkem této kontrole:  
  
    -   Kontrola, zda je obor.  
  
    -   Pokud je obor, hodnota <xref:System.Transactions.EnterpriseServicesInteropOption> výčet předané v případě oboru bylo původně vytvořeno je zaškrtnuto.  
  
    -   Pokud <xref:System.Transactions.EnterpriseServicesInteropOption> výčtu je nastavena na <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, transakce modelu COM + (<xref:System.EnterpriseServices> transakce) má přednost před <xref:System.Transactions> transakce v místním úložišti spravované vlákno.  
  
         Pokud hodnota je nastavena <xref:System.Transactions.EnterpriseServicesInteropOption.None>, <xref:System.Transactions> transakce v místním úložišti spravované vlákno přednost.  
  
         Pokud je hodnota <xref:System.Transactions.EnterpriseServicesInteropOption.Full>, existuje pouze jeden transakce a je transakce modelu COM +.  
  
2.  Hodnota <xref:System.Transactions.TransactionScopeOption> výčet předaných v <xref:System.Transactions.TransactionScope> konstruktor je zaškrtnuto. Určuje, zda je nutné vytvořit novou transakci.  
  
3.  Pokud novou transakci má být vytvořen, následující hodnoty <xref:System.Transactions.EnterpriseServicesInteropOption> za následek:  
  
    -   <xref:System.Transactions.EnterpriseServicesInteropOption.Full>: je vytvořen transakcí spojený s kontextem modelu COM +.  
  
    -   <xref:System.Transactions.EnterpriseServicesInteropOption.None>: <xref:System.Transactions> transakce je vytvořen.  
  
    -   <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>: Pokud je kontext modelu COM +, transakcí je vytvořen a připojit ke kontextu.  
  
 Následující tabulka znázorňuje kontext služby Enterprise (ES) a transakční obor, který vyžaduje, aby transakce pomocí <xref:System.Transactions.EnterpriseServicesInteropOption> výčtu.  
  
|Kontext ES|Žádná|Automatické|Do bloku|  
|----------------|----------|---------------|----------|  
|Výchozí kontext|Výchozí kontext|Výchozí kontext|Vytvořit nový <br />transakční kontextu|  
|Jiné než výchozí kontext|Udržovat kontextu klienta|Vytvořit nový transakční kontext|Vytvořit nový transakční kontext|  
  
 Následující tabulka popisuje, co okolí transakce je, daný konkrétní <xref:System.EnterpriseServices> kontextu a transakční obor, který vyžaduje, aby transakce pomocí <xref:System.Transactions.EnterpriseServicesInteropOption> výčtu.  
  
|Kontext ES|Žádná|Automatické|Do bloku|  
|----------------|----------|---------------|----------|  
|Výchozí kontext|ST|ST|ES|  
|Jiné než výchozí kontext|ST|ES|ES|  
  
 V tabulce:  
  
-   ST znamená spravuje okolí transakce oboru <xref:System.Transactions>, nezávisle na jakékoli <xref:System.EnterpriseServices> daného kontextu transakce, které mohou být k dispozici.  
  
-   ES znamená, že oboru okolí transakce je stejná jako <xref:System.EnterpriseServices> transakce daného kontextu.
