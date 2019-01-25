---
title: Ukázka technologie serializace obecných typů služby webového
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 27e0a7621bc77b62e36a0bbbdfa25f0ec3778798
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636579"
---
# <a name="web-services-generics-serialization-technology-sample"></a>Ukázka technologie serializace obecných typů služby webového
[Stáhněte si ukázky](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 Tento příklad ukazuje, jak používat a řídit serializace obecných typů v webové služby ASP.NET.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>K vytvoření vzorku pomocí sady Visual Studio  
  
1.  Otevřít Visual Studio a vyberte **nový web** z **souboru** nabídky.  
  
2.  V **nový web** dialogového okna, vyberte v levém podokně požadovanou programovací jazyk a potom v pravém podokně vyberte **webová služba ASP.NET**.  
  
3.  Klikněte na tlačítko **Procházet** a přejděte do podadresáře \CS\GenericsService.  
  
4.  Vyberte Service.asmx k otevření souboru v sadě Visual Studio.  
  
5.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
> [!NOTE]
>  Prvních pět kroků v tomto seznamu jsou volitelné. Modul runtime rozhraní .NET Framework, bude automaticky generovat webové služby první čas, kdy je požadována služba.  
  
> [!NOTE]
>  Následující kroky jsou nutné k vytvoření vzorku.  
  
1.  Otevřít [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] a přejděte do podadresáře \CS.  
  
2.  Klikněte pravým tlačítkem na ikonu podadresáři GenericsService a vyberte **sdílení a zabezpečení**.  
  
3.  V **sdílení na webu** kartu, vyberte možnost **sdílet tuto složku**.  
  
> [!IMPORTANT]
>  Poznamenejte si název virtuálního adresáře, který je uveden v **aliasy** podokno, protože je budete potřebovat ke spuštění ukázky.  
  
### <a name="to-build-the-sample-using-internet-information-services"></a>K vytvoření vzorku pomocí Internetové informační služby  
  
1.  Otevřít **Internetová informační služba** správy modulu snap-in a rozbalení **weby**.  
  
2.  Klepněte na položku **výchozí webový server**vyberte **nový**a pak vyberte **virtuální adresář?** vytvořit **Průvodce vytvořením virtuálního adresáře**.  
  
3.  Klikněte na tlačítko **Další**, zadejte veřejné alias pro virtuální adresář a klikněte na tlačítko **Další**.  
  
4.  Zadejte cestu k adresáři, kam jste uložili vzorku (obvykle podadresář \CS\GenericsService) a klikněte na tlačítko **Další**. Klikněte na tlačítko **Další** dokončete průvodce.  
  
> [!IMPORTANT]
>  Poznamenejte si název virtuálního adresáře, který je uveden v **Alias** podokno, protože je budete potřebovat ke spuštění ukázky.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete okno prohlížeče a vyberte jeho adresa.  
  
2.  Typ `http://localhost/[virtual directory]/Service.asmx`, kde `[virtual directory]` představuje virtuální adresář, který jste vytvořili při sestavení vzorku.  
  
## <a name="remarks"></a>Poznámky  
 Ukázka zobrazí výchozí stránka technologie ASP.NET, která obsahuje odkazy na definice webové služby. Můžete přizpůsobit zobrazení kromě Změna zdrojového kódu webové služby. Další informace najdete v tématu [klienty vytváření XML webové služby](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- <xref:System.Web.Services>
- <xref:System.Xml.Serialization>
- [Serializace](../../../docs/standard/serialization/index.md)
- [Webové služby XML vytvořené pomocí ASP.NET a klienty webové služby XML](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)
