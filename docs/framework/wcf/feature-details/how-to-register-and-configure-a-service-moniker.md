---
title: 'Postupy: registrace a konfigurace Monikeru služby'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: 1d245327c1e7d53de9a88c93ff0399d8e231a1df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493312"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>Postupy: registrace a konfigurace Monikeru služby
Před použitím monikeru služby Windows Communication Foundation (WCF) v rámci aplikace modelu COM s typem kontrakt, musíte zaregistrovat požadované s atributy typy v modelu COM a nakonfigurovat aplikaci COM a moniker s požadovaná vazba konfigurace.  
  
### <a name="to-register-the-required-attributed-types-with-com"></a>Registrace vyžaduje s atributy typy v modelu COM  
  
1.  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj k načtení metadat kontrakt ze služby WCF. To generuje zdrojový kód je sestavení klienta WCF a konfiguračního souboru aplikace klienta.  
  
2.  Ujistěte se, že typy v sestavení jsou označeny jako `ComVisible`. Uděláte to tak, přidejte následující atribut do souboru AssemblyInfo.cs v projektu sady Visual Studio.  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  Zkompilujte spravovaného klienta WCF jako sestavení se silným názvem. To vyžaduje podepsání pomocí páru kryptografických klíčů. Další informace najdete v tématu [podepsání sestavení se silným názvem](http://go.microsoft.com/fwlink/?LinkId=94874) v příručce pro vývojáře .NET.  
  
4.  Použijte nástroj Assembly Registration (Regasm.exe) s `/tlb` možnost zaregistrovat typy v sestavení s COM.  
  
5.  Použijte nástroj globální mezipaměti sestavení (Gacutil.exe) pro přidání sestavení do globální mezipaměti sestavení.  
  
    > [!NOTE]
    >  Podepisování sestavení a její přidání do globální mezipaměti sestavení jsou volitelné kroky, ale jejich může zjednodušit proces načítání sestavení za běhu na správném místě.  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>Konfigurace aplikace modelu COM a Přezdívka s konfigurací požadovaná vazba  
  
-   Umístěte definice vazba (vygenerované [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) v konfiguračním souboru aplikace generovaného klienta) v konfiguračním souboru aplikace klienta. Například pro Visual Basic 6.0 spustitelný soubor s názvem CallCenterClient.exe, musí být umístěny konfiguraci do souboru s názvem CallCenterConfig.exe.config ve stejném adresáři jako spustitelný soubor. Klientská aplikace teď můžete použít přezdívka. Všimněte si, že pokud pomocí jedné z standardní typy poskytované WCF vazby není potřeba Konfigurace vazeb.  
  
     Následující typ je registrován.  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     Aplikace je vystaven pomocí `wsHttpBinding` vazby. Pro daný typ a konfiguraci aplikace se používají následující příklad Přezdívka řetězce.  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     Můžete použít některý z těchto Přezdívka řetězců z v rámci aplikace Visual Basic 6.0, po přidání odkaz na sestavení, které obsahuje `IMathService` typů, jak je znázorněno v následujícím ukázkovém kódu.  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     V tomto příkladu definici konfigurace vazeb `Binding1` je uložen v vhodně pojmenované konfigurační soubor pro klientská aplikace, jako je například vb6appname.exe.config.  
  
    > [!NOTE]
    >  Můžete podobný kódu v C#, jazyka C++ nebo jiné aplikace rozhraní .NET jazyka.  
  
    > [!NOTE]
    >  : Pokud Přezdívka je poškozený nebo pokud služba není dostupná, volání `GetObject` vrátí chybu "Neplatná syntaxe". Pokud se zobrazí tato chyba, ujistěte se, kterou používáte Přezdívka je správný a služba není k dispozici.  
  
     I když toto téma se zaměřuje na použití monikeru služby z kódu jazyka Visual Basic 6.0, je použití monikeru služby z jiných jazyků. Když pomocí Přezdívka z jazyka C++ kódové Svcutil.exe generované sestavení by měly naimportovány s "named_guids – no_namespace – raw_interfaces_only –" jak je znázorněno v následujícím kódu.  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     To definice importované rozhraní upraví tak, aby všechny metody vrátit `HResult`. Všechny ostatní vrácené hodnoty se převedou na výstupní parametry. Celkový provoz metody zůstává stejná. To umožňuje určit, proč k výjimce při volání metody na proxy serveru. Tato funkce je dostupná pouze z kódu jazyka C++.  
  
## <a name="see-also"></a>Viz také  
 [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
