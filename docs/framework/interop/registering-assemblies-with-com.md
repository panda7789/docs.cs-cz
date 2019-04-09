---
title: Registrování sestav pomocí modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 834652318d4cb1cbcebe27a922d210ef87026ed5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169023"
---
# <a name="registering-assemblies-with-com"></a>Registrování sestav pomocí modelu COM
Spustíte nástroj příkazového řádku, volá se, [nástroj registrace sestavení (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) k registraci nebo zrušení registrace sestavení pro použití v modelu COM. Abyste klientům modelu COM použít třídy rozhraní .NET Framework transparentně RegAsm.exe přidá informace o třídě do systémového registru. <xref:System.Runtime.InteropServices.RegistrationServices> Třída poskytuje ekvivalentní funkce.  
  
 Před aktivací klientů modelu COM, musí být spravované součásti zaregistrovaný v registru Windows. V následující tabulce jsou uvedeny klíče, které Regasm.exe obvykle přidá do registru Windows. (000000 určuje skutečnou hodnotu GUID).  
  
|GUID|Popis|Klíč registru|  
|----------|-----------------|------------------|  
|IDENTIFIKÁTOR CLSID|Identifikátor třídy|HKEY_CLASSES_ROOT\CLSID\\{000…000}|  
|IID|Identifikátor rozhraní|HKEY_CLASSES_ROOT\Interface\\{000…000}|  
|LIBID|Identifikátor knihovny|HKEY_CLASSES_ROOT\TypeLib\\{000…000}|  
|ProgID|Programový identifikátor|HKEY_CLASSES_ROOT\000…000|  
  
 V části HKCR\CLSID\\{0000... 0000} klíč, výchozí hodnota je nastavena na identifikátor ProgID, třídy a jsou přidány dva nové pojmenovaných hodnot, třídy a sestavení. Modul runtime přečte hodnotu sestavení z registru a předává je do překladače sestavení modulu runtime. Překladač sestavení se pokusí najít sestavení, na základě informací o sestavení, jako je například název a číslo verze. Sestavení pro sestavení překladač snaze o nalezení sestavení, musí být v jednom z následujících umístění:  
  
-   Globální mezipaměti sestavení (musí být sestavení se silným názvem).  
  
-   V adresáři aplikace. Sestavení načtená z cesty aplikace jsou pouze přístupné z této aplikace.  
  
-   Cestě soubor zadaný **/ codebase** možnost Regasm.exe.  
  
 RegAsm.exe vytvoří také InProcServer32 klíče pod HKCR\CLSID\\{0000... 0000} klíč. Výchozí hodnota klíče je nastavena na název knihovny DLL, která inicializuje modul common language runtime (Mscoree.dll).  
  
## <a name="examining-registry-entries"></a>Ověření položky registru  
 Komunikace s objekty COM poskytuje objekt pro vytváření implementaci standardní třída pro vytvoření instance libovolné třídy rozhraní .NET Framework. Klienti mohou volat **DllGetClassObject** na spravovanou knihovnu DLL k získání objektu pro vytváření tříd a vytvořit objekty, stejně jako jakoukoli jinou součástí modelu COM.  
  
 Pro `InprocServer32` podklíč, zobrazí se místo tradiční knihovně typů modelu COM k označení, zda modul common language runtime vytvoří spravovaný objekt odkaz na knihovny Mscoree.dll.  
  
## <a name="see-also"></a>Viz také:

- [Vystavení komponent architektury .NET Framework pro COM](exposing-dotnet-components-to-com.md)
- [Postupy: Odkazování na typy .NET z modelu COM](how-to-reference-net-types-from-com.md)
- [Volání objektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [Nasazení aplikace pro přístup COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
