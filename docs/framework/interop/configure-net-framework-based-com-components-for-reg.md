---
title: 'Postupy: Konfigurace bezregistrační aktivace komponent využívajících rozhraní .NET Framework'
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: dedf5ab51ab5cf9befb5bd183968388406df4e5b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181466"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Postupy: Konfigurace bezregistrační aktivace komponent využívajících rozhraní .NET Framework
Aktivace bez registrace pro součásti založené na rozhraní .NET Framework je jen o něco složitější než pro komponenty MODELU COM. Nastavení vyžaduje dva manifesty:  
  
- Aplikace modelu COM musí mít manifest aplikace ve stylu win32 k identifikaci spravované součásti.  
  
- Součásti založené na rozhraní .NET Framework musí mít manifest součásti pro informace o aktivaci potřebné za běhu.  
  
 Toto téma popisuje, jak přidružit manifest aplikace k aplikaci; přidružení manifestu součásti k součásti; a vložit manifest součásti do sestavy.  
  
### <a name="to-create-an-application-manifest"></a>Vytvoření manifestu aplikace  
  
1. Pomocí editoru XML vytvořte (nebo upravte) manifest aplikace vlastněný aplikací modelu COM, která spolupracuje s jednou nebo více spravovanými součástmi.  
  
2. Na začátek souboru vložte následující standardní záhlaví:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Informace o elementech manifestu a jejich atributech naleznete v [tématu Manifesty aplikací](/windows/desktop/SbsCs/application-manifests).  
  
3. Identifikujte vlastníka manifestu. V následujícím příkladu `myComApp` vlastní soubor manifestu verze 1.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="msil"
      />  
    ```  
  
4. Identifikujte závislá sestavení. V následujícím příkladu `myComApp` `myManagedComp`závisí na .  
  
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
  
5. Uložte a pojmenujte soubor manifestu. Název manifestu aplikace je název spustitelného souboru sestavení následovaný rozšířením manifestu .manifest. Například název souboru manifestu aplikace pro myComApp.exe je myComApp.exe.manifest.  
  
 Manifest aplikace můžete nainstalovat do stejného adresáře jako aplikace COM. Případně jej můžete přidat jako prostředek do souboru EXE aplikace. Další informace naleznete v tématu [O souběžných sestaveních](/windows/desktop/SbsCs/about-side-by-side-assemblies-).  
  
#### <a name="to-create-a-component-manifest"></a>Vytvoření manifestu komponenty  
  
1. Pomocí editoru XML vytvořte manifest součásti popisující spravované sestavení.  
  
2. Na začátek souboru vložte následující standardní záhlaví:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. Identifikujte vlastníka souboru. Prvek `<assemblyIdentity>` prvku `<dependentAssembly>` v souboru manifestu aplikace se musí shodovat s prvkem v manifestu komponenty. V následujícím příkladu `myManagedComp` verze 1.2.3.4 vlastní soubor manifestu.  
  
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
  
4. Identifikujte každou třídu v sestavení. Pomocí `<clrClass>` prvku jednoznačně identifikovat každou třídu ve spravovaném sestavení. Prvek, který je dílčím `<assembly>` prvkem prvku, má atributy popsané v následující tabulce.  
  
    |Atribut|Popis|Požaduje se|  
    |---------------|-----------------|--------------|  
    |`clsid`|Identifikátor, který určuje třídu, která má být aktivována.|Ano|  
    |`description`|Řetězec, který informuje uživatele o součásti. Prázdný řetězec je výchozí.|Ne|  
    |`name`|Řetězec, který představuje spravovanou třídu.|Ano|  
    |`progid`|Identifikátor, který má být použit pro aktivaci s pozdní vazbou.|Ne|  
    |`threadingModel`|Model zřetězení modelu COM. "Obojí" je výchozí hodnota.|Ne|  
    |`runtimeVersion`|Určuje verzi clr (COMMON Language runtime), která má být používána. Pokud tento atribut nezadáte a CLR ještě není načten, je komponenta načtena s nejnovější nainstalovanou clr před CLR verze 4. Pokud zadáte v1.0.3705, v1.1.4322 nebo v2.0.50727, verze se automaticky převrátí na nejnovější nainstalovanou verzi CLR před CLR verze 4 (obvykle v2.0.50727). Pokud je již načtena jiná verze clr a zadaná verze může být načtena v procesu vedle sebe, zadaná verze je načtena. v opačném případě se použije načtený CLR. To může způsobit selhání zatížení.|Ne|  
    |`tlbid`|Identifikátor knihovny typů, která obsahuje informace o typu třídy.|Ne|  
  
     Všechny značky atributů rozlišují malá a velká písmena. Identifikátory CLSID, identifikátory ProgID, modely vláken a verzi za běhu můžete získat zobrazením exportované knihovny typů pro sestavení pomocí aplikace OLE/COM ObjectViewer (Oleview.exe).  
  
     Následující manifest komponenty identifikuje `testClass1` dvě `testClass2`třídy a .  
  
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
  
5. Uložte a pojmenujte soubor manifestu. Název manifestu komponenty je název knihovny sestavení následovaný příponou .manifest. Například myManagedComp.dll je myManagedComp.manifest.  
  
 Manifest součásti je nutné vložit jako prostředek do sestavy.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Vložení manifestu součásti do spravované sestavy  
  
1. Vytvořte skript prostředků, který obsahuje následující příkaz:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     V tomto `myManagedComp.manifest` příkazu je název manifestu komponenty, který je vložen. V tomto příkladu je `myresource.rc`název souboru skriptu .  
  
2. Zkompilujte skript pomocí kompilátoru prostředků systému Microsoft Windows (Rc.exe). Do příkazového řádku zadejte následující příkaz:  
  
     `rc myresource.rc`  
  
     Rc.exe vytvoří `myresource.res` soubor prostředků.  
  
3. Znovu zkompilujte zdrojový soubor sestavení a zadejte soubor prostředků pomocí možnosti **/win32res:**  
  
    `/win32res:myresource.res`  
  
     Opět `myresource.res` je název souboru prostředků obsahující vložené prostředky.  
  
## <a name="see-also"></a>Viz také

- [Bezregistrační zprostředkovatel komunikace s objekty COM](registration-free-com-interop.md)
- [Požadavky na interop COM Interop bez registrace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))
- [Konfigurace komponent modelu COM pro aktivaci bez registrace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))
- [Registrace-Free Aktivace . Komponenty založené na NET: Návod](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))
