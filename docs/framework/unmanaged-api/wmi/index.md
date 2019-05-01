---
title: WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)
description: Shrnuje rozhraní .NET Framework nespravovaného rozhraní API pro informace o čítači rozhraní WMI a výkonu.
author: rpetrusha
ms.author: ronpet
ms.date: 11/06/2017
ms.openlocfilehash: bbf22496098f848cc7c55652198d792c6f631c15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049307"
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Windows Management Instrumentation (WMI) a z čítačů výkonu (referenční dokumentace nespravovaného rozhraní API)

Nespravované rozhraní API .NET Framework WMI a čítače výkonu se skládá ze sady funkcí, které obalují volání [nativní Windows Management Instrumentation rozhraní API](/windows/desktop/WmiSdk/com-api-for-wmi). To umožňuje vyvíjet nástroje a knihovny pro správu a monitorování systémů vzdáleného počítače.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

Toto rozhraní API zahrnuje následující funkce:

| Funkce | Popis |
|---------|---------|
| [Funkce BeginEnumeration](beginenumeration.md) | Enumerátor obnoví na začátku výčet vlastností objektu rozhraní WMI. |
| [Funkce BeginMethodEnumeration](beginmethodenumeration.md) |  Začíná výčet metody dostupné pro objekt. |
| [Funkce BlessIWbemServices](blessiwbemservices.md) | Určuje, jestli se přihlašovací údaje uživatele odkudkoli přístup k dané služby IWbem třídy. |
| [Funkce BlessIWbemServicesObject](blessiwbemservicesobject.md) | Určuje, jestli se přihlašovací údaje uživatele povolení přístupu k zadanému objektu služby IWbem. |
| [Funkce Clone](clone.md) | Vrátí nový objekt, který je kompletní klon aktuálního objektu. |
| [Funkce CloneEnumWbemClassObject](cloneenumwbemclassobject.md) | Vytvoří kopii logické tohoto čítače, zachovat své aktuální pozici ve výčtu. |
| [Funkce CompareTo](compareto.md) | Porovná objekt na jiný objekt správy Windows. |
| [ConnectServerWmi – funkce](connectserverwmi.md) | Připojení přes DCOM k oboru názvů WMI vytvoří v zadaném počítači. |
| [CreateClassEnumWmi – funkce](createclassenumwmi.md) | Vrátí enumerátor pro všechny třídy, které splňují kritéria zadaná výběru. |
| [CreateInstanceEnumWmi – funkce](createinstanceenumwmi.md) | Vrátí enumerátor, který vrátí instance dané třídy, které splňují kritéria zadaná výběru. |
| [Funkce Delete](delete.md) | Odstraní zadanou vlastnost z definice třídy a všechny jeho kvalifikátory. |
| [Funkce DeleteMethod](deletemethod.md) | Odstraní zadanou metodu z definice třídy CIM. |
| [Funkce EndEnumeration](endenumeration.md) | Ukončí sekvenci výčtu. |
| [Funkce EndMethodEnumeration](endmethodenumeration.md) | Ukončí sekvenci výčet tím, že volání [funkce BeginMethodEnumeration](beginmethodenumeration.md). |
| [Funkce ExecNotificationQueryWmi](execnotificationquerywmi.md) | Provede dotaz přijímat události. |
| [Funkce ExecQueryWmi](execquerywmi.md) | Spustí dotaz pro načtení objektů. |
| [Funkce FormatFromRawValue](formatfromrawvalue.md) | Převede jednu hodnotu hrubý výkon při zpracování dat pro zadaný formát nebo dvě hodnoty hrubý výkon při zpracování dat, pokud převod formátu podle času. |
| [Funkce Get](get.md) | Načte hodnotu zadané vlastnosti, pokud existuje. |
| [GetCurrentApartmentType function](getcurrentapartmenttype.md) | Získá typ objektu apartment, ve kterém je spuštěn volající. |
| [GetDemultiplexedStub – funkce](getdemultiplexedstub.md) | Vytvoří pomáhat klientovi v přijetí byla zahájena asynchronní volání ze správy službou Windows Server pro předávání jímky objektu. |
| [GetErrorInfo – funkce](geterrorinfo.md) | Načte informace o chybě z předchozího volání funkce. |
| [Funkce GetMethod](getmethod.md) | Načte informace o zadané metodě. |
| [Funkce GetMethodOrigin](getmethodorigin.md) | Určuje třídy, ve kterém je deklarována metodu. |
| [Funkce GetMethodQualifierSet](getmethodqualifierset.md) | Načte kvalifikátor nastavit pro konkrétní metody. |
| [Funkce GetNames](getnames.md) | Načte podmnožinu nebo všechny názvy vlastností objektu. |
| [Funkce GetObjectText](getobjecttext.md) | Vrátí textovou vykreslování objektu v syntaxi MOF. |
| [Funkce GetPropertyHandle](getpropertyhandle.md) | Vrátí jedinečný popisovač identifikující vlastnosti. |
| [Funkce GetPropertyOrigin](getpropertyorigin.md) | Určuje třídy, ve kterém je deklarována vlastnost. |
| [GetPropertyQualifierSet – funkce](getpropertyqualifierset.md) | Načte kvalifikátor nastavit určité vlastnosti.  |
| [GetQualifierSet – funkce](getqualifierset.md) | Načte kvalifikátor, nastavte pro instanci třídy nebo definice třídy. |
| [InheritsFrom – funkce](inheritsfrom.md) | Určuje, zda aktuální třídy nebo instance je odvozena od třídy zadaný nadřazený prvek. |
| [Initialize – funkce](initialize.md) | Provede inicializaci služby WMI. |
| [Další funkce](next.md) | Načte další vlastnosti ve výčtu. |
| [NextMethod – funkce](nextmethod.md) | Načte další metody ve výčtu. |
| [PUT – funkce](put.md) | Pojmenovanou vlastnost nastaví na novou hodnotu. |
| [PutClassWmi – funkce](putclasswmi.md) | Vytvoří novou třídu nebo aktualizuje nějakou existující. |
| [PutInstanceWmi – funkce](putinstancewmi.md) | Vytvoří nebo aktualizuje instance existující třídy. Instance se zapisují do úložiště služby WMI. |
| [PutMethod – funkce](putmethod.md) | Vytvoří metodu. |
| [QualifierSet_BeginEnumeration – funkce](qualifierset-beginenumeration.md) | Návrat na začátek výčtu enumerátor kvalifikátory objektu. |
| [QualifierSet_Delete – funkce](qualifierset-delete.md) | Odstraní zadaný kvalifikátor podle názvu.  |
| [QualifierSet_EndEnumeration – funkce](qualifierset-endenumeration.md) | Ukončí výčet začal s voláním `QualifierSet_BeginEnumeration` funkce. |
| [QualifierSet_Get – funkce](qualifierset-get.md) | Získá zadaný s názvem kvalifikátoru.  |
| [QualifierSet_GetNames function](qualifierset-getnames.md) | Načte názvy všech kvalifikátory nebo zadané kvalifikátory, které jsou k dispozici z aktuální objekt nebo vlastnost. |
| [QualifierSet_Next function](qualifierset-next.md) | Načte další kvalifikátor ve výčtu, který spustil pomocí volání [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkce. |
| [QualifierSet_Put – funkce](qualifierset-put.md) | Zapíše s názvem kvalifikátoru a hodnotu. |
| [ResetSecurity – funkce](resetsecurity.md) | Přiřadí zadaný zosobnění pro aktuální vlákno. |
| [SetSecurity – funkce](setsecurity.md) | Získá token zosobnění spojený s aktuálním vláknem. |
| [SpawnDerivedClass – funkce](spawnderivedclass.md) | Vytvoří objekt nově odvozené třídy ze zadaného objektu. |
| [SpawnInstance – funkce](spawninstance.md) | Vytvoří novou instanci třídy. |
| [VerifyClient – funkce](verifyclientkey.md) | Zajistí, že klíč klienta bude mít správné zabezpečení. |
| [WritePropertyValue – funkce](writepropertyvalue.md) | Zapíše zadaný počet bajtů na vlastnost identifikovaný popisovač vlastnosti. |

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace nespravovaného rozhraní API](../index.md)
