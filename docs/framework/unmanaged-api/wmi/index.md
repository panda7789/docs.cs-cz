---
title: WMI a čítače výkonu (Reference nespravovaného rozhraní API)
description: Shrnuje .NET Framework nespravované rozhraní API pro informace o čítačích výkonu a rozhraní WMI.
ms.date: 11/06/2017
ms.openlocfilehash: f28cd25ee6c3511dc5ac8a6dd4076c81f43fe74a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127411"
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Rozhraní WMI (Windows Management Instrumentation) (WMI) a čítače výkonu (nespravované reference rozhraní API)

Rozhraní API .NET Framework rozhraní WMI a čítače výkonu nespravované rozhraní API se skládá ze sady funkcí, které zabalí volání do [nativního rozhraní api rozhraní WMI (Windows Management Instrumentation)](/windows/desktop/WmiSdk/com-api-for-wmi). Umožňuje vyvíjet nástroje a knihovny, které spravují a monitorují vzdálené počítačové systémy.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

Rozhraní API obsahuje následující funkce:

| Funkce | Popis |
|---------|---------|
| [Funkce BeginEnumeration](beginenumeration.md) | Obnoví enumerátor na začátek výčtu vlastností objektu WMI. |
| [Funkce BeginMethodEnumeration](beginmethodenumeration.md) |  Spustí výčet metod, které jsou k dispozici pro objekt. |
| [Funkce BlessIWbemServices](blessiwbemservices.md) | Určuje, zda přihlašovací údaje uživatele povolují přístup k zadané třídě služby IWbem. |
| [Funkce BlessIWbemServicesObject](blessiwbemservicesobject.md) | Určuje, jestli přihlašovací údaje uživatele povolují přístup k zadanému objektu služby IWbem. |
| [Funkce Clone](clone.md) | Vrátí nový objekt, který je úplným klonem aktuálního objektu. |
| [Funkce CloneEnumWbemClassObject](cloneenumwbemclassobject.md) | Vytvoří logickou kopii enumerátoru a uchová jeho aktuální pozici ve výčtu. |
| [Funkce CompareTo](compareto.md) | Porovná objekt s jiným objektem správy systému Windows. |
| [ConnectServerWmi – funkce](connectserverwmi.md) | Vytvoří připojení prostřednictvím modelu DCOM k oboru názvů WMI v zadaném počítači. |
| [CreateClassEnumWmi – funkce](createclassenumwmi.md) | Vrátí enumerátor pro všechny třídy, které odpovídají zadaným kritériím výběru. |
| [CreateInstanceEnumWmi – funkce](createinstanceenumwmi.md) | Vrátí enumerátor, který vrátí instance zadané třídy, které splňují zadaná kritéria výběru. |
| [Funkce Delete](delete.md) | Odstraní zadanou vlastnost z definice třídy a všech jejích kvalifikátorů. |
| [Funkce DeleteMethod](deletemethod.md) | Odstraní zadanou metodu z definice třídy CIM. |
| [Funkce EndEnumeration](endenumeration.md) | Ukončí sekvenci výčtu. |
| [Funkce EndMethodEnumeration](endmethodenumeration.md) | Ukončí sekvenci výčtu spuštěnou voláním [funkce BeginMethodEnumeration](beginmethodenumeration.md). |
| [Funkce ExecNotificationQueryWmi](execnotificationquerywmi.md) | Spustí dotaz pro příjem událostí. |
| [Funkce ExecQueryWmi](execquerywmi.md) | Spustí dotaz pro načtení objektů. |
| [Funkce FormatFromRawValue](formatfromrawvalue.md) | Převede jednu nezpracovaná hodnota dat výkonu na určený formát nebo dvě nezpracované hodnoty dat výkonu, pokud je převod formátu založený na čase. |
| [Funkce Get](get.md) | Načte zadanou hodnotu vlastnosti, pokud existuje. |
| [GetCurrentApartmentType – funkce](getcurrentapartmenttype.md) | Načte typ objektu apartment, ve kterém je volající spuštěn. |
| [GetDemultiplexedStub – funkce](getdemultiplexedstub.md) | Vytvoří jímku objektu pro překládání objektů, která klientovi pomůže přijímat asynchronní volání ze správy systému Windows. |
| [GetErrorInfo – funkce](geterrorinfo.md) | Načte informace o chybě z předchozího volání funkce. |
| [Funkce GetMethod](getmethod.md) | Načte informace o zadané metodě. |
| [Funkce GetMethodOrigin](getmethodorigin.md) | Určuje třídu, ve které je deklarována metoda. |
| [Funkce GetMethodQualifierSet](getmethodqualifierset.md) | Načte kvalifikátor sady pro konkrétní metodu. |
| [Funkce GetNames](getnames.md) | Načte buď podmnožinu, nebo všechny názvy vlastností objektu. |
| [Funkce GetObjectText](getobjecttext.md) | Vrátí textové vykreslování objektu v syntaxi MOF. |
| [Funkce GetPropertyHandle](getpropertyhandle.md) | Vrací jedinečný popisovač, který identifikuje vlastnost. |
| [Funkce GetPropertyOrigin](getpropertyorigin.md) | Určuje třídu, ve které je deklarována vlastnost. |
| [GetPropertyQualifierSet – funkce](getpropertyqualifierset.md) | Načte kvalifikátor sady pro konkrétní vlastnost.  |
| [GetQualifierSet – funkce](getqualifierset.md) | Načte kvalifikátor sady pro instanci třídy nebo definici třídy. |
| [InheritsFrom – funkce](inheritsfrom.md) | Určuje, zda aktuální třída nebo instance je odvozena ze zadané nadřazené třídy. |
| [Initialize – funkce](initialize.md) | Provede inicializaci rozhraní WMI. |
| [Funkce Next](next.md) | Načte další vlastnost ve výčtu. |
| [NextMethod – funkce](nextmethod.md) | Načte další metodu ve výčtu. |
| [Put – funkce](put.md) | Nastaví vlastnost s názvem na novou hodnotu. |
| [PutClassWmi – funkce](putclasswmi.md) | Vytvoří novou třídu nebo aktualizuje stávající. |
| [PutInstanceWmi – funkce](putinstancewmi.md) | Vytvoří nebo aktualizuje instanci existující třídy. Instance je zapsána do úložiště rozhraní WMI. |
| [PutMethod – funkce](putmethod.md) | Vytvoří metodu. |
| [QualifierSet_BeginEnumeration – funkce](qualifierset-beginenumeration.md) | Obnoví enumerátor kvalifikátorů objektu na začátek výčtu. |
| [QualifierSet_Delete – funkce](qualifierset-delete.md) | Odstraní zadaný kvalifikátor podle názvu.  |
| [QualifierSet_EndEnumeration – funkce](qualifierset-endenumeration.md) | Ukončí výčet zahájený voláním funkce `QualifierSet_BeginEnumeration`. |
| [QualifierSet_Get – funkce](qualifierset-get.md) | Získá zadaný pojmenovaný kvalifikátor.  |
| [QualifierSet_GetNames – funkce](qualifierset-getnames.md) | Načte názvy všech kvalifikátorů nebo určených kvalifikátorů, které jsou k dispozici z aktuálního objektu nebo vlastnosti. |
| [QualifierSet_Next – funkce](qualifierset-next.md) | Načte další kvalifikátor ve výčtu, který začal voláním funkce [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) . |
| [QualifierSet_Put – funkce](qualifierset-put.md) | Zapíše pojmenovaný kvalifikátor a hodnotu. |
| [ResetSecurity – funkce](resetsecurity.md) | Přiřadí zadaný token zosobnění aktuálnímu vláknu. |
| [SetSecurity – funkce](setsecurity.md) | Načte token zosobnění přidružený k aktuálnímu vláknu. |
| [SpawnDerivedClass – funkce](spawnderivedclass.md) | Vytvoří nově odvozený objekt třídy ze zadaného objektu. |
| [SpawnInstance – funkce](spawninstance.md) | Vytvoří novou instanci třídy. |
| [VerifyClient – funkce](verifyclientkey.md) | Zajišťuje, aby měl klíč klienta správné zabezpečení. |
| [WritePropertyValue – funkce](writepropertyvalue.md) | Zapíše zadaný počet bajtů na vlastnost identifikovanou popisovačem vlastnosti. |

## <a name="see-also"></a>Viz také:

- [Nespravované reference rozhraní API](../index.md)
