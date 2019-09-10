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
ms.openlocfilehash: baabff187fb8a22aea37c4fb4c1dc11a680d3bb8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70853851"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Postupy: Konfigurace komponent COM využívajících rozhraní .NET Framework pro aktivaci bez registrace
Aktivace bez registrace pro komponenty založené na .NET Framework je poněkud složitější než pro součásti modelu COM. Instalační program vyžaduje dva manifesty:  
  
- Aby bylo možné identifikovat spravovanou součást, musí mít aplikace modelu COM manifest aplikace ve stylu Win32.  
  
- Komponenty založené na .NET Framework musí mít manifest součásti pro informace o aktivaci potřebné v době běhu.  
  
 Toto téma popisuje, jak přidružit manifest aplikace k aplikaci. Přidružte manifest součásti k komponentě. a vložte manifest součásti do sestavení.  
  
### <a name="to-create-an-application-manifest"></a>Vytvoření manifestu aplikace  
  
1. Pomocí editoru XML vytvořte (nebo upravte) manifest aplikace vlastněný aplikací modelu COM, která je v provozu s jednou nebo více spravovanými komponentami.  
  
2. Vložte následující standardní hlavičku na začátek souboru:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Informace o prvcích manifestu a jejich atributech naleznete v tématu [manifesty aplikací](/windows/desktop/SbsCs/application-manifests).  
  
3. Identifikujte vlastníka manifestu. V následujícím příkladu `myComApp` verze 1 vlastní soubor manifestu.  
  
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
  
5. Uložte a pojmenujte soubor manifestu. Název manifestu aplikace je název spustitelného souboru sestavení následovaný příponou. manifest. Například název souboru manifestu aplikace pro myComApp. exe je myComApp. exe. manifest.  
  
 Manifest aplikace můžete nainstalovat do stejného adresáře jako aplikace modelu COM. Případně ho můžete přidat jako prostředek do souboru. exe aplikace. Další informace najdete v tématu [o souběžných sestaveních](/windows/desktop/SbsCs/about-side-by-side-assemblies-).  
  
#### <a name="to-create-a-component-manifest"></a>Vytvoření manifestu součásti  
  
1. Pomocí editoru XML vytvořte manifest součásti pro popis spravovaného sestavení.  
  
2. Vložte následující standardní hlavičku na začátek souboru:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. Identifikujte vlastníka souboru. Element `<assemblyIdentity>` `<dependentAssembly>` elementu v souboru manifestu aplikace se musí shodovat s prvkem v manifestu součásti. V následujícím příkladu `myManagedComp` je verze 1.2.3.4 vlastníkem souboru manifestu.  
  
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
  
4. Identifikujte každou třídu v sestavení. `<clrClass>` Pomocí elementu jednoznačně Identifikujte jednotlivé třídy ve spravovaném sestavení. Element, který je dílčím prvkem `<assembly>` elementu, má atributy popsané v následující tabulce.  
  
    |Atribut|Popis|Požadováno|  
    |---------------|-----------------|--------------|  
    |`clsid`|Identifikátor, který určuje třídu, která má být aktivována.|Ano|  
    |`description`|Řetězec, který informuje uživatele o komponentě. Výchozí hodnota je prázdný řetězec.|Ne|  
    |`name`|Řetězec, který představuje spravovanou třídu.|Ano|  
    |`progid`|Identifikátor, který se má použít pro aktivaci s pozdní vazbou.|Ne|  
    |`threadingModel`|Model vláken modelu COM. Výchozí hodnota je "obojí".|Ne|  
    |`runtimeVersion`|Určuje verzi modulu CLR (Common Language Runtime), která se má použít. Pokud tento atribut nezadáte a CLR již není načten, komponenta je načtena s nejnovějším nainstalovaným modulem CLR před modulem CLR verze 4. Pokud zadáte v 1.0.3705, v 1.1.4322 nebo v 2.0.50727, verze se automaticky vrátí k nejnovější nainstalované verzi CLR před CLR verze 4 (obvykle v 2.0.50727). Pokud je již načtena jiná verze modulu CLR a zadaná verze může být načtena souběžně v rámci procesu, je načtena zadaná verze; v opačném případě je použit načtený modul CLR. To může způsobit selhání načtení.|Ne|  
    |`tlbid`|Identifikátor knihovny typů, která obsahuje informace o typu třídy.|Ne|  
  
     U všech značek atributů se rozlišují velká a malá písmena. Identifikátory CLSID, ProgID, modely vláken a verze modulu runtime lze získat zobrazením exportované knihovny typů pro sestavení pomocí technologie OLE/COM ObjectViewer (Oleview. exe).  
  
     Následující manifest komponenty identifikuje dvě třídy, `testClass1` a. `testClass2`  
  
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
  
5. Uložte a pojmenujte soubor manifestu. Název manifestu součásti je název knihovny sestavení následovaný příponou. manifest. Například myManagedComp. dll je myManagedComp. manifest.  
  
 Manifest součásti je nutné vložit jako prostředek v sestavení.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Vložení manifestu součásti do spravovaného sestavení  
  
1. Vytvořte skript prostředků, který obsahuje následující příkaz:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     V tomto příkazu je `myManagedComp.manifest` název manifestu součásti, který se má vložit. V tomto příkladu je `myresource.rc`název souboru skriptu.  
  
2. Zkompilujte skript pomocí kompilátoru prostředků Microsoft Windows (RC. exe). V příkazovém řádku zadejte následující příkaz:  
  
     `rc myresource.rc`  
  
     RC. exe vytvoří `myresource.res` soubor prostředků.  
  
3. Zkompilujte zdrojový soubor sestavení znovu a zadejte soubor prostředků pomocí možnosti **parametr/win32res** :  
  
    `/win32res:myresource.res`  
  
     `myresource.res` Znovu je název souboru prostředků obsahujícího vložené prostředky.  
  
## <a name="see-also"></a>Viz také:

- [Bezregistrační zprostředkovatel komunikace s objekty COM](registration-free-com-interop.md)
- [Požadavky na zprostředkovatele komunikace s objekty COM bez registrace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))
- [Konfigurace komponent modelu COM pro aktivaci bez registrace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))
- [Aktivace aplikace bez registrace. Komponenty založené na síti: Návod](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))
