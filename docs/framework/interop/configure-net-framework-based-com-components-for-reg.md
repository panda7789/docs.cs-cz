---
title: 'Postupy: Konfigurace komponent COM využívajících rozhraní .NET Framework pro aktivaci bez registrace'
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea62f7dc5c47f52f94567857427e7add929b8b1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643397"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Postupy: Konfigurace komponent COM využívajících rozhraní .NET Framework pro aktivaci bez registrace
Bezregistrační aktivace komponent využívajících rozhraní .NET Framework je jenom o něco složitější než pro komponenty modelu COM. Instalace vyžaduje dva manifesty:  
  
- Aplikace modelu COM musí mít aplikace manifest Win32 – vizuální styl k identifikaci spravované součásti.  
  
- Komponenty založené na platformě .NET musí mít manifestu součásti aktivace informace potřebné v době běhu.  
  
 Toto téma popisuje, jak přidružit aplikaci; manifest aplikace manifest součásti přidružit komponentu; a vložení manifestu do komponenty v sestavení.  
  
### <a name="to-create-an-application-manifest"></a>Chcete-li vytvořit manifest aplikace  
  
1. Pomocí editoru XML, vytvořit (nebo upravit) manifest aplikace vlastněné aplikací modelu COM, který je spolupráce s jedním nebo více spravovaných komponenty.  
  
2. Vložte následující standardní hlavičku na začátek souboru:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Informace o manifestu prvky a jejich atributů najdete v tématu [manifesty aplikací](/windows/desktop/SbsCs/application-manifests).  
  
3. Určete vlastníka manifest. V následujícím příkladu `myComApp` verze 1 vlastníkem souboru manifestu.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4. Identifikujte závislá sestavení. V následujícím příkladu `myComApp` závisí na `myManagedComp`.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="x86"   
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myManagedComp"   
                        version="6.0.0.0"   
                        processorArchitecture="X86"   
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5. Uložit a název souboru manifestu. Název manifestu aplikace je název sestavení spustitelného souboru a příponu .manifest. Například je název souboru manifestu aplikace pro myComApp.exe myComApp.exe.manifest.  
  
 Manifest aplikace můžete nainstalovat ve stejném adresáři jako aplikace modelu COM. Alternativně můžete přidat ho jako prostředek do souboru .exe vaší aplikace. Další informace najdete další informace najdete v tématu [o sestavení vedle sebe](/windows/desktop/SbsCs/about-side-by-side-assemblies-).  
  
#### <a name="to-create-a-component-manifest"></a>K vytvoření manifestu komponenty  
  
1. Pomocí editoru XML, vytvoření manifestu komponenty k popisu spravovaných sestavení.  
  
2. Vložte následující standardní hlavičku na začátek souboru:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. Určete vlastníka souboru. `<assemblyIdentity>` Elementu `<dependentAssembly>` prvku v souboru manifestu aplikace musí odpovídat názvu v manifestu součásti. V následujícím příkladu `myManagedComp` verzi 1.2.3.4 je vlastníkem souboru manifestu.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4. Identifikujte jednotlivé třídy v sestavení. Použití `<clrClass>` element k jednoznačné identifikaci každé třídě spravované sestavení. Element, který je podřízený z `<assembly>` element, atributy jsou popsané v následující tabulce.  
  
    |Atribut|Popis|Požadováno|  
    |---------------|-----------------|--------------|  
    |`clsid`|Identifikátor, který určuje třídy, která má být aktivován.|Ano|  
    |`description`|Řetězec, který informuje uživatele o komponentě. Výchozím nastavením je prázdný řetězec.|Ne|  
    |`name`|Řetězec, který představuje spravovanou třídu.|Ano|  
    |`progid`|Identifikátor, který má být použit pro aktivaci s pozdní vazbou.|Ne|  
    |`threadingModel`|Model COM vláken. Výchozí hodnota je "I".|Ne|  
    |`runtimeVersion`|Určuje verze společného jazyka runtime (CLR) používat. Pokud tento atribut není zadán, a CLR dosud není načtený, komponenta načtena s nainstalovanou CLR před CLR verze 4. Pokud zadáte v1.0.3705, v1.1.4322 nebo v2.0.50727, verze automaticky provede dopředné obnovení na nejnovější CLR verze před CLR verze 4 (obvykle v2.0.50727). Pokud je již načtena jiná verze modulu CLR a zadaná verze je možné načíst vedle sebe v procesu, je uvedena verze je načten. v opačném případě se používá načtené CLR. Tato akce může způsobit chyby načítání.|Ne|  
    |`tlbid`|Identifikátor, který obsahuje typ informace o třídě knihovny typů.|Ne|  
  
     Všechny značky atributů jsou malá a velká písmena. Můžete získat CLSID, ProgID, práce s vlákny modely a verze modulu runtime zobrazením exportované knihovny typů pro sestavení ObjectViewer OLE/COM (Oleview.exe).  
  
     Následující komponenty manifest identifikuje dvě třídy `testClass1` a `testClass2`.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"   
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5. Uložit a název souboru manifestu. Název manifestu součásti je název sestavení knihovny následovaný příponou .manifest. Například myManagedComp.dll je myManagedComp.manifest.  
  
 Manifest součásti musí vložen jako prostředek v sestavení.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Pro vložení manifestu komponenty spravovaných sestavení  
  
1. Vytvořte skript prostředků, který obsahuje následující příkaz:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     V tomto prohlášení `myManagedComp.manifest` je název manifestu komponenty jsou vložené. V tomto příkladu je název souboru skriptu `myresource.rc`.  
  
2. Kompilace skriptu s použitím Microsoft Windows Resource Compiler (Rc.exe). V příkazovém řádku zadejte následující příkaz:  
  
     `rc myresource.rc`  
  
     Vytvoří RC.exe `myresource.res` souboru prostředků.  
  
3. Znovu zkompilovat sestavení zdrojového souboru a zadejte soubor prostředků pomocí **/win32res** možnost:  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     Opět `myresource.res` je název souboru prostředku, který obsahuje integrovaný prostředek.  
  
## <a name="see-also"></a>Viz také:

- [Bezregistrační zprostředkovatel komunikace s objekty COM](registration-free-com-interop.md)
- [Požadavky pro zprostředkovatele komunikace s objekty COM bez registrace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))
- [Konfigurace komponent COM pro aktivaci bez registrace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))
- [Bezregistrační aktivace. Na základě NET součásti: Názorný postup](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))
