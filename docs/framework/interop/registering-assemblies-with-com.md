---
title: Registrování sestav pomocí modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
ms.openlocfilehash: 9ff24a5705058d4e303b3b64b454ced8548053a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113811"
---
# <a name="registering-assemblies-with-com"></a>Registrování sestav pomocí modelu COM
Můžete spustit nástroj příkazového řádku nazvaný [Nástroj pro registraci sestavení (Regasm. exe)](../tools/regasm-exe-assembly-registration-tool.md) k registraci nebo zrušení registrace sestavení pro použití s modelem COM. Nástroj Regasm. exe přidává do systémového registru informace o třídě, takže klienti modelu COM mohou použít třídu .NET Framework transparentně. <xref:System.Runtime.InteropServices.RegistrationServices> Třída poskytuje ekvivalentní funkce.  
  
 Spravovaná součást musí být registrována v registru systému Windows, aby ji bylo možné aktivovat z klienta modelu COM. V následující tabulce jsou uvedeny klíče, které nástroj Regasm. exe obvykle přidává do registru systému Windows. (000000 označuje skutečnou hodnotu GUID.)  
  
|GUID|Popis|Klíč registru|  
|----------|-----------------|------------------|  
|CLSID|Identifikátor třídy|HKEY_CLASSES_ROOT \CLSID\\{000... 10000|  
|IDENTIFIKÁTOR|Identifikátor rozhraní|HKEY_CLASSES_ROOT \Interface\\{000... 10000|  
|LIBID|Identifikátor knihovny|HKEY_CLASSES_ROOT \TypeLib\\{000... 10000|  
|ProgID|Programový identifikátor|HKEY_CLASSES_ROOT \ 000... 10000|  
  
 Pod HKCR\CLSID\\{0000... 0000} klíč, výchozí hodnota je nastavená na ProgID třídy a přidají se dvě nové pojmenované hodnoty, třídy a sestavení. Modul runtime přečte hodnotu sestavení z registru a předá ho Překladači sestavení modulu runtime. Překladač sestavení se pokusí vyhledat sestavení na základě informací o sestavení, jako je název a číslo verze. Aby mohl překladač sestavení vyhledat sestavení, musí být sestavení v jednom z následujících umístění:  
  
- Globální mezipaměť sestavení (musí být sestavení se silným názvem).  
  
- V adresáři aplikace. Sestavení načtená z cesty aplikace jsou přístupná pouze z této aplikace.  
  
- Společně s cestou k souboru zadaným pomocí možnosti **/codebase** pro Regasm. exe.  
  
 Nástroj Regasm. exe také vytvoří klíč InProcServer32 pod HKCR\CLSID\\{0000... 0000} klíč. Výchozí hodnota pro klíč je nastavena na název knihovny DLL, která Inicializuje modul CLR (Common Language Runtime) (mscoree. dll).  
  
## <a name="examining-registry-entries"></a>Ověření položky registru  
 Zprostředkovatel komunikace s objekty COM poskytuje standardní implementaci továrny tříd pro vytvoření instance libovolné .NET Framework třídy. Klienti mohou volat **DllGetClassObject** na spravované knihovně DLL pro získání objektu pro vytváření tříd a vytváření objektů stejně, jako by to byly s jinou komponentou modelu COM.  
  
 V případě `InprocServer32` podklíče se zobrazí odkaz na Mscoree. dll namísto tradiční knihovny typů modelu COM k označení toho, že modul CLR (Common Language Runtime) vytvoří spravovaný objekt.  
  
## <a name="see-also"></a>Viz také

- [Vystavení komponent architektury .NET Framework pro COM](exposing-dotnet-components-to-com.md)
- [Postupy: Odkazování na typy .NET z modelu COM](how-to-reference-net-types-from-com.md)
- [Volání objektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [Nasazení aplikace pro přístup k modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
