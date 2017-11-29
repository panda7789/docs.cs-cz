---
title: "Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)"
description: "Shrnuje rozhraní .NET Framework nespravovaného rozhraní API pro informace o rozhraní WMI a výkonu čítače."
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.date: 11/06/2017
ms.topic: article-type-from-white-list
ms.prod: .net-framework
ms.devlang: cpp
ms.openlocfilehash: 461d90aaf5beca1c0f1d1965ce0ea07411e56e79
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2017
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Windows Management Instrumentation (WMI) a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)

Obsahuje sadu funkcí, které balí volání nespravovaného rozhraní API služby WMI rozhraní .NET Framework a čítače výkonu [nativní Windows Management Instrumentation API](https://msdn.microsoft.com/library/aa389276(v=vs.85).aspx). Umožňuje vyvíjet nástroje a knihovny, které spravovat a monitorovat systémy vzdáleného počítače.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
Rozhraní API obsahuje následující funkce:

| Funkce | Popis |
|---------|---------|
| [Funkce BeginEnumeration – funkce](beginenumeration.md) | Návrat na začátek výčtu WMI vlastnosti objektu enumerátor. |
| [BeginMethodEnumeration – funkce](beginmethodenumeration.md) |  Zahájí výčet dostupné metody pro objekt. |
| [BlessIWbemServices – funkce](blessiwbemservices.md) | Určuje, zda přihlašovací údaje uživatele povolit přístup k zadané služby IWbem třídy. |
| [BlessIWbemServicesObject – funkce](blessiwbemservicesobject.md) | Určuje, zda přihlašovací údaje uživatele povolit přístup k zadanému objektu služby IWbem. |
| [Clone – funkce](clone.md) | Vrátí nový objekt, který je kompletní klonem aktuálního objektu. |
| [CloneEnumWbemClassObject – funkce](cloneenumwbemclassobject.md) | Vytvoří kopii logické enumerátor zachovat své aktuální pozici ve výčtu. |
| [CompareTo – funkce](compareto.md) | Porovná objekt k jinému objektu správy systému Windows. |
| [ConnectServerWmi – funkce](connectserverwmi.md) | Vytvoří připojení přes DCOM k oboru názvů WMI v zadaném počítači. |
| [CreateClassEnumWmi – funkce](createclassenumwmi.md) | Vrátí enumerátor pro všechny třídy, které splňují kritéria zadaná výběru. |
| [CreateInstanceEnumWmi – funkce](createinstanceenumwmi.md) | Vrátí enumerátor, který vrátí intances dané třídy, které splňují kritéria zadaná výběr. |
| [Odstranit – funkce](delete.md) | Odstraní zadané vlastnosti z definice třídy a všechny jeho kvalifikátory. |
| [Metoda DeleteMethod – funkce](deletemethod.md) | Odstraní zadanou metodu z definice třídy CIM. |
| [Funkce EndEnumeration – funkce](endenumeration.md) | Ukončí v sekvenci výčtu. | 
| [EndMethodEnumeration – funkce](endmethodenumeration.md) | Ukončí v sekvenci výčtu spuštění voláním [BeginMethodEnumeration funkce](beginmethodenumeration.md). |
| [ExecNotificationQueryWmi – funkce](execnotificationquerywmi.md) | Provede dotaz přijímat události. |
| [ExecQueryWmi – funkce](execquerywmi.md) | Provede dotaz pro načtení objektů. |
| [FormatFromRawValue – funkce](formatfromrawvalue.md) | Převede jednu hodnotu hrubý výkon při zpracování dat pro zadaný formát nebo dvě hodnoty hrubý výkon při zpracování dat, pokud převod formátu je založené na čase. | 
| [Get – funkce](get.md) | Načte hodnotu zadanou vlastnost, pokud existuje. |
| [GetCurrentApartmentType – funkce](getcurrentapartmenttype.md) | Načte typu apartment, ve kterém je prováděna volající. |
| [GetDemultiplexedStub – funkce](getdemultiplexedstub.md) | Vytvoří předávání podřízený objekt klienta jako pomůcku při přijímání asynchronní volání od Správa systému Windows. |
| [GetErrorInfo – funkce](geterrorinfo.md) | Načte informace o chybě z předchozího volání funkce. | 
| [Getmethod – funkce](getmethod.md) | Načte informace o zadanou metodu. | 
| [GetMethodOrigin – funkce](getmethodorigin.md) | Určuje třídu, ve kterém je deklarovaná metodu. |
| [GetMethodQualifierSet – funkce](getmethodqualifierset.md) | Načte kvalifikátor nastavit pro konkrétní metody. |
| [GetNames – funkce](getnames.md) | Načte podmnožinu nebo všechny názvy vlastností objektu. |
| [GetObjectText – funkce](getobjecttext.md) | Vrátí textovou vykreslování objektu v syntaxi MOF. | 
| [GetPropertyHandle – funkce](getpropertyhandle.md) | Vrací jedinečný popisovač, který identifikuje vlastnost. |
| [GetPropertyOrigin – funkce](getpropertyorigin.md) | Určuje třídu, ve kterém je deklarovaná vlastnost. |
| [GetPropertyQualifierSet – funkce](getpropertyqualifierset.md) | Načte kvalifikátor nastavit určité vlastnosti.  |
| [GetQualifierSet – funkce](getqualifierset.md) | Načte kvalifikátor pro instanci třídy nebo definici třídy. |
| [InheritsFrom – funkce](inheritsfrom.md) | Určuje, zda aktuální třídy nebo instance je odvozena od třídy zadaný nadřazený. |
| [Initialize – funkce](initialize.md) | Provede inicializaci rozhraní WMI. |
| [Další funkce](next.md) | Načte další vlastnosti ve výčtu. | 
| [NextMethod – funkce](nextmethod.md) | Načte metodu další ve výčtu. |
| [PUT – funkce](put.md) | Nastaví vlastnost s názvem na novou hodnotu. |
| [PutClassWmi – funkce](putclasswmi.md) | Vytvoří novou třídu nebo aktualizuje stávající. |
| [PutInstanceWmi – funkce](putinstancewmi.md) | Vytvoří nebo aktualizuje existující třídy instance. Instance je zapsán do úložiště služby WMI. |
| [PutMethod – funkce](putmethod.md) | Vytvoří metodu. |
| [QualifierSet_BeginEnumeration – funkce](qualifierset-beginenumeration.md) | Návrat na začátek výčtu enumerátor kvalifikátory objektu. |
| [QualifierSet_Delete – funkce](qualifierset-delete.md) | Odstraní zadaný kvalifikátor podle názvu.  |
| [QualifierSet_EndEnumeration – funkce](qualifierset-endenumeration.md) | Ukončí výčtu zahájena volání `QualifierSet_BeginEnumeration` funkce. |
| [QualifierSet_Get – funkce](qualifierset-get.md) | Získá zadaný s názvem kvalifikátor.  |
| [QualifierSet_GetNames – funkce](qualifierset-getnames.md) | Načte názvy všech kvalifikátory nebo zadaný kvalifikátory, které jsou k dispozici na aktuální objekt nebo vlastnost. |
| [QualifierSet_Next – funkce](qualifierset-next.md) | Načte další kvalifikátor v výčet, který je spuštěn s volání [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkce. |
| [QualifierSet_Put – funkce](qualifierset-put.md) | Zapíše kvalifikátor s názvem a hodnotou. |
| [ResetSecurity – funkce](resetsecurity.md) | Přiřadí token poskytnutý zosobnění aktuální vlákno. |
| [SetSecurity – funkce](setsecurity.md) | Načte token zosobnění přidružené k aktuální vlákno. |
| [SpawnDerivedClass – funkce](spawnderivedclass.md) | Vytvoří objekt nově odvozených tříd ze zadaného objektu. | 
| [SpawnInstance – funkce](spawninstance.md) | Vytvoří novou instanci třídy. |   
| [VerifyClient – funkce](verifyclientkey.md) | Zajišťuje, že klíč klienta má správné zabezpečení. |
| [WritePropertyValue – funkce](writepropertyvalue.md) | Zapíše zadaný počet bajtů na vlastnost identifikovaný popisovače vlastnosti. |

 ## <a name="see-also"></a>Viz také
[Referenční dokumentace nespravovaného rozhraní API](../index.md) 