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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 744ce1f2810eee025f071cafaa71e473b6ed4c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Postupy: Konfigurace bezregistrační aktivace komponent využívajících rozhraní .NET Framework
Bezregistrační aktivace komponent využívajících rozhraní .NET Framework je pouze mírně složitěji, než je pro komponenty modelu COM. Instalace vyžaduje dva manifesty:  
  
-   Aplikace modelu COM musí mít manifest aplikace Win32 stylu k identifikaci spravované součásti.  
  
-   Součásti rozhraní .NET framework pro musí mít manifest součásti pro informace o aktivaci za běhu.  
  
 Toto téma popisuje, jak přidružit manifest aplikace aplikace. manifest součásti přidružit součást; a vložení do sestavení manifest součásti.  
  
### <a name="to-create-an-application-manifest"></a>Chcete-li vytvořit manifest aplikace  
  
1.  Pomocí editoru XML, vytvořit (nebo upravit) manifest aplikace, které jsou ve vlastnictví aplikací modelu COM, která je spolupráce s jedním nebo více spravovaných součásti.  
  
2.  Na začátek souboru vložte následující standardní hlavičku:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Informace o manifestu elementy a jejich atributy najdete v tématu [manifesty aplikací](https://msdn.microsoft.com/library/windows/desktop/aa374191.aspx).  
  
3.  Identifikujte vlastník manifestu. V následujícím příkladu `myComApp` verze 1 vlastní soubor manifestu.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  Identifikujte závislá sestavení. V následujícím příkladu `myComApp` závisí na `myManagedComp`.  
  
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
  
5.  Uložte a název souboru manifestu. Název manifest aplikace je název spustitelného souboru sestavení a příponu manifest. Například je název souboru manifestu aplikace pro myComApp.exe myComApp.exe.manifest.  
  
 Manifest aplikace můžete nainstalovat do stejného adresáře jako aplikaci COM. Alternativně můžete ho přidat jako prostředek do souboru .exe aplikace. Další informace najdete další informace najdete v tématu [o souběžně sdílená sestavení](https://msdn.microsoft.com/library/windows/desktop/ff951640.aspx).  
  
#### <a name="to-create-a-component-manifest"></a>Chcete-li vytvořit manifest součásti  
  
1.  Pomocí editoru XML, vytvoření manifestu součástí popsat spravované sestavení.  
  
2.  Na začátek souboru vložte následující standardní hlavičku:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  Určete vlastníka souboru. `<assemblyIdentity>` Element `<dependentAssembly>` element v souboru manifestu aplikace musí odpovídat názvu v manifestu součásti. V následujícím příkladu `myManagedComp` verze 1.2.3.4 vlastní soubor manifestu.  
  
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
  
4.  Identifikujte každá třída v sestavení. Použití `<clrClass>` element k jednoznačné identifikaci každé třídě spravované sestavení. Element, který je dílčí prvek z `<assembly>` elementu, má atributy popsané v následující tabulce.  
  
    |Atribut|Popis|Požadováno|  
    |---------------|-----------------|--------------|  
    |`clsid`|Identifikátor, který určuje třídu, která chcete aktivovat.|Ano|  
    |`description`|Řetězec, který informuje uživatele o komponentu. Výchozí je prázdný řetězec.|Ne|  
    |`name`|Řetězec, který představuje spravované třídy.|Ano|  
    |`progid`|Identifikátor, který má být použit pro aktivaci pozdní vazbu.|Ne|  
    |`threadingModel`|Model COM vláken. "I" je výchozí hodnota.|Ne|  
    |`runtimeVersion`|Určuje společné jazykové verzi modulu runtime (CLR) používat. Pokud nezadáte tento atribut a dosud není načtený modulu CLR, součást je načtena s nainstalovanou CLR před CLR verze 4. Pokud zadáte v1.0.3705, v1.1.4322 nebo v2.0.50727, verze automaticky posunete na nejnovější nainstalované verze CLR před CLR verze 4 (obvykle v2.0.50727). Pokud už je načtený jinou verzi modulu CLR a zadaná verze mohou být načteny vedle sebe v procesu, je zadaná verze načten. načíst CLR, jinak se používá. To může způsobit selhání načtení.|Ne|  
    |`tlbid`|Identifikátor knihovny typů, který obsahuje informace o typu o třídě.|Ne|  
  
     Všechny značky atribut rozlišují velká a malá písmena. Můžete získat CLSID, ProgID, dělení na vlákna modely a verze modulu runtime zobrazením knihovně exportovaný typ pro toto sestavení s ObjectViewer OLE/COM (Oleview.exe).  
  
     Následující součást manifest identifikuje dvě třídy `testClass1` a `testClass2`.  
  
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
  
5.  Uložte a název souboru manifestu. Název manifestu součástí je název a příponu manifest sestavení knihovny. Například myManagedComp.dll je myManagedComp.manifest.  
  
 Manifest součásti musíte vložit jako prostředek v sestavení.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Manifest součásti vložit do spravované sestavení.  
  
1.  Vytvořte prostředek skript, který obsahuje následující příkaz:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     V tomto prohlášení `myManagedComp.manifest` je název manifestu součástí jeho vkládání. V tomto příkladu je název souboru skriptu `myresource.rc`.  
  
2.  Zkompilujte skriptu pomocí kompilátor prostředků systému Microsoft Windows (Rc.exe). V příkazovém řádku zadejte následující příkaz:  
  
     `rc myresource.rc`  
  
     Vytvoří RC.exe `myresource.res` souboru prostředků.  
  
3.  Kompilace sestavení zdrojový soubor znovu a určete soubor prostředků pomocí **/win32res** možnost:  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     Znovu `myresource.res` je název souboru prostředků obsahující vložený prostředek.  
  
## <a name="see-also"></a>Viz také  
 [Bezregistrační zprostředkovatel komunikace s objekty COM](registration-free-com-interop.md)  
 [Požadavky pro zprostředkovatel komunikace s objekty COM bez registrace](https://msdn.microsoft.com/library/0c43bc57-eecf-4e6c-8114-490141cce4da(v=vs.100)))  
 [Konfigurace komponenty modelu COM bez registrace aktivace](https://msdn.microsoft.com/library/bfe9b02f-d964-4784-960e-a1f94692fbfe(v=vs.100)))  
 [Bezregistrační aktivace. Na základě NET komponenty: Návod](https://msdn.microsoft.com/library/ms973915.aspx)
