---
title: Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)
description: Shrnuje nespravované rozhraní API rozhraní .NET Framework pro rozhraní WMI a informace o čítači výkonu.
ms.date: 11/06/2017
ms.openlocfilehash: f28cd25ee6c3511dc5ac8a6dd4076c81f43fe74a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127411"
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Wmi (WMI) a čítače výkonu (nespravované odkazy na rozhraní API)

Nespravované rozhraní API rozhraní .NET Framework WMI a Performance Counters se skládá ze sady funkcí, které zalamují volání [do nativního rozhraní API pro službu W MANAGEMENT INSTRUMENTACE](/windows/desktop/WmiSdk/com-api-for-wmi). Umožňuje vyvíjet nástroje a knihovny, které spravují a monitorují vzdálené počítačové systémy.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

Rozhraní API obsahuje následující funkce:

| Funkce | Popis |
|---------|---------|
| [Funkce BeginEnumeration](beginenumeration.md) | Obnoví čítač výčtu na začátek výčtu vlastností objektu služby WMI. |
| [Funkce BeginMethodEnumeration](beginmethodenumeration.md) |  Začíná výčet metod, které jsou k dispozici pro objekt. |
| [Funkce BlessIWbemServices](blessiwbemservices.md) | Označuje, zda pověření uživatele povolit přístup k zadané IWbemServices třídy. |
| [Funkce BlessIWbemServicesObject](blessiwbemservicesobject.md) | Označuje, zda pověření uživatele povolují přístup k určenému objektu služby IWbem. |
| [Funkce Clone](clone.md) | Vrátí nový objekt, který je úplným klonem aktuálního objektu. |
| [Funkce CloneEnumWbemClassObject](cloneenumwbemclassobject.md) | Vytvoří logickou kopii čítače výčtu, zachování jeho aktuální pozici ve výčtu. |
| [Funkce CompareTo](compareto.md) | Porovná objekt s jiným objektem správy systému Windows. |
| [Funkce ConnectServerWmi](connectserverwmi.md) | Vytvoří připojení prostřednictvím souboru DCOM k oboru názvů wmi v zadaném počítači. |
| [CreateClassEnumWmi](createclassenumwmi.md) | Vrátí čítač výčtu pro všechny třídy, které splňují zadaná kritéria výběru. |
| [CreateInstanceEnumWmi](createinstanceenumwmi.md) | Vrátí čítač výčtu, který vrací instance zadané třídy, které splňují zadaná kritéria výběru. |
| [Funkce Delete](delete.md) | Odstraní zadanou vlastnost z definice třídy a všechny její kvalifikátory. |
| [Funkce DeleteMethod](deletemethod.md) | Odstraní zadanou metodu z definice třídy CIM. |
| [Funkce EndEnumeration](endenumeration.md) | Ukončí pořadí výčtu. |
| [Funkce EndMethodEnumeration](endmethodenumeration.md) | Ukončí posloupnost výčtu spuštěnou voláním [funkce BeginMethodEnumeration .](beginmethodenumeration.md) |
| [Funkce ExecNotificationQueryWmi](execnotificationquerywmi.md) | Spustí dotaz pro příjem událostí. |
| [Funkce ExecQueryWmi](execquerywmi.md) | Spustí dotaz k načtení objektů. |
| [Funkce FormatFromRawValue](formatfromrawvalue.md) | Převede jednu nezpracovaná hodnota dat výkonu na zadaný formát nebo dvě nezpracovaná hodnoty dat výkonu, pokud je převod formátu založen na čase. |
| [Funkce Get](get.md) | Načte zadanou hodnotu vlastnosti, pokud existuje. |
| [GetCurrentApartmentType](getcurrentapartmenttype.md) | Načte typ apartment, ve kterém volající provádí. |
| [GetDemultiplexedStub](getdemultiplexedstub.md) | Vytvoří jímku pro předávání objektů, která pomáhá klientovi přijímat asynchronní volání ze správy systému Windows. |
| [GetErrorInfo](geterrorinfo.md) | Načte informace o chybě z předchozího volání funkce. |
| [Funkce GetMethod](getmethod.md) | Načte informace o zadané metodě. |
| [Funkce GetMethodOrigin](getmethodorigin.md) | Určuje třídu, ve které je deklarována metoda. |
| [Funkce GetMethodQualifierSet](getmethodqualifierset.md) | Načte kvalitátor nastavit pro konkrétní metodu. |
| [Funkce GetNames](getnames.md) | Načte podmnožinu nebo všechny názvy vlastností objektu. |
| [Funkce GetObjectText](getobjecttext.md) | Vrátí textové vykreslování objektu v syntaxi MOF. |
| [Funkce GetPropertyHandle](getpropertyhandle.md) | Vrátí jedinečný popisovač, který identifikuje vlastnost. |
| [Funkce GetPropertyOrigin](getpropertyorigin.md) | Určuje třídu, ve které je deklarována vlastnost. |
| [GetPropertyQualifierSet](getpropertyqualifierset.md) | Načte kvalifikátor nastavena pro konkrétní vlastnost.  |
| [GetQualifierSet](getqualifierset.md) | Načte kvalifikátor nastavenou pro instanci třídy nebo definici třídy. |
| [InheritsFrom,](inheritsfrom.md) | Určuje, zda aktuální třída nebo instance pochází z zadané nadřazené třídy. |
| [Inicializovat funkci](initialize.md) | Provede inicializaci wmi. |
| [Další funkce](next.md) | Načte další vlastnost ve výčtu. |
| [NextMethod](nextmethod.md) | Načte další metodu ve výčtu. |
| [Funkce Put](put.md) | Nastaví pojmenovanou vlastnost na novou hodnotu. |
| [PutClassWmi](putclasswmi.md) | Vytvoří novou třídu nebo aktualizuje existující. |
| [PutInstanceWmi](putinstancewmi.md) | Vytvoří nebo aktualizuje instanci existující třídy. Instance je zapsána do úložiště služby WMI. |
| [PutMethod](putmethod.md) | Vytvoří metodu. |
| [QualifierSet_BeginEnumeration funkce](qualifierset-beginenumeration.md) | Obnoví čítač výčtu kvalifikátory objektu na začátek výčtu. |
| [QualifierSet_Delete funkce](qualifierset-delete.md) | Odstraní zadaný kvalifikátor podle názvu.  |
| [QualifierSet_EndEnumeration funkce](qualifierset-endenumeration.md) | Ukončí výčet, který byl zahájen `QualifierSet_BeginEnumeration` voláním funkce. |
| [QualifierSet_Get funkce](qualifierset-get.md) | Získá zadaný pojmenovaný kvalifikátor.  |
| [QualifierSet_GetNames funkce](qualifierset-getnames.md) | Načte názvy všech kvalifikátorů nebo určených kvalifikátorů, které jsou k dispozici z aktuálního objektu nebo vlastnosti. |
| [QualifierSet_Next funkce](qualifierset-next.md) | Načte další kvalifikátor ve výčtu, který začal s voláním [funkce QualifierSet_BeginEnumeration.](qualifierset-beginenumeration.md) |
| [QualifierSet_Put funkce](qualifierset-put.md) | Zapíše pojmenovaný kvalifikátor a hodnotu. |
| [Funkce ResetSecurity](resetsecurity.md) | Přiřadí zadaný token zosobnění aktuálnímu vláknu. |
| [Funkce SetSecurity](setsecurity.md) | Načte token zosobnění přidružený k aktuálnímu vláknu. |
| [SpawnDerivedClass](spawnderivedclass.md) | Vytvoří nově odvozený objekt třídy z určeného objektu. |
| [SpawnInstance](spawninstance.md) | Vytvoří novou instanci třídy. |
| [Ověřit funkci Klienta](verifyclientkey.md) | Zajišťuje, že klientský klíč má správné zabezpečení. |
| [WritePropertyValue](writepropertyvalue.md) | Zapíše zadaný počet bajtů do vlastnosti identifikované popisovačem vlastnosti. |

## <a name="see-also"></a>Viz také

- [Nespravovaný odkaz na rozhraní API](../index.md)
