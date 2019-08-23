---
title: Ukázka technologie serializace obecných typů ve webových službách
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 467bfe1fd9eb8a0222385c34cb29a90df00dc937
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960752"
---
# <a name="web-services-generics-serialization-technology-sample"></a>Ukázka technologie serializace obecných typů ve webových službách
[Ukázka stažení](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 Tento příklad ukazuje, jak používat a řídit serializaci generických typů v ASP.NET webových službách.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>K vytvoření vzorku pomocí sady Visual Studio  
  
1. Otevřete Visual Studio a v nabídce **soubor** vyberte **Nový web** .  
  
2. V dialogovém okně **Nový web** vyberte v levém podokně požadovaný programovací jazyk a potom v pravém podokně vyberte **ASP.NET webová služba**.  
  
3. Klikněte na **Procházet** a přejděte do podadresáře \CS\GenericsService.  
  
4. Vyberte Service.asmx k otevření souboru v sadě Visual Studio.  
  
5. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
> [!NOTE]
> Prvních pět kroků v tomto seznamu jsou volitelné. Modul runtime rozhraní .NET Framework, bude automaticky generovat webové služby první čas, kdy je požadována služba.  
  
> [!NOTE]
> Následující kroky jsou nutné k vytvoření vzorku.  
  
1. Otevřete Průzkumníka souborů a přejděte do podadresáře \CS.  
  
2. Klikněte pravým tlačítkem na ikonu podadresáře GenericsService a vyberte **sdílení a zabezpečení**.  
  
3. Na kartě **sdílení webu** vyberte **sdílet tuto složku**.  
  
> [!IMPORTANT]
> Poznamenejte si název virtuálního adresáře, který je uvedený v podokně **aliasy** , protože ho budete potřebovat ke spuštění ukázky.  
  
### <a name="to-build-the-sample-using-internet-information-services"></a>K vytvoření vzorku pomocí Internetové informační služby  
  
1. Otevřete modul snap-in Správa **Internetová informační služba** a rozbalte **weby**.  
  
2. Klikněte levým na **výchozí web**, vyberte **Nový**a potom vyberte **virtuální adresář?** a vytvořte tak **Průvodce vytvořením virtuálního adresáře**.  
  
3. Klikněte na **Další**, zadejte veřejný alias pro virtuální adresář a klikněte na **Další**.  
  
4. Zadejte cestu k adresáři, do kterého jste ukázku uložili (obvykle podadresář \CS\GenericsService), a klikněte na **Další**. Průvodce dokončíte kliknutím na tlačítko **Další** .  
  
> [!IMPORTANT]
> Poznamenejte si název virtuálního adresáře, který je uvedený v podokně **alias** , protože ho budete potřebovat ke spuštění ukázky.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1. Otevřete okno prohlížeče a vyberte jeho adresa.  
  
2. Typ `http://localhost/[virtual directory]/Service.asmx`, kde `[virtual directory]` představuje virtuální adresář, který jste vytvořili při vytvoření ukázky.  
  
## <a name="remarks"></a>Poznámky  
 Ukázka zobrazí výchozí stránka technologie ASP.NET, která obsahuje odkazy na definice webové služby. Můžete přizpůsobit zobrazení kromě Změna zdrojového kódu webové služby. Další informace naleznete v tématu [sestavování klientů webové služby XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- <xref:System.Web.Services>
- <xref:System.Xml.Serialization>
- [Serializace](../../../docs/standard/serialization/index.md)
- [Webové služby XML vytvořené pomocí ASP.NET a klientů webové služby XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))
