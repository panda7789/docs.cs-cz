---
title: Webové služby Obecné serializace technologie ukázky
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 29cfa8f66f4b465d30c85c6944b8f3d94203f489
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585613"
---
# <a name="web-services-generics-serialization-technology-sample"></a>Webové služby Obecné serializace technologie ukázky
[Stažení ukázky](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 Tento příklad ukazuje, jak používat a řízení serializace obecných typů ve webové služby ASP.NET.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>K vytvoření vzorku pomocí sady Visual Studio  
  
1.  Otevřete Visual Studio a vyberte **nový web** z **souboru** nabídky.  
  
2.  V **nový web** dialogové okno, v levém podokně vyberte požadovaný programovací jazyk a pak v pravém podokně vyberte **webovou službu ASP.NET**.  
  
3.  Klikněte na tlačítko **Procházet** a přejděte do podadresáři \CS\GenericsService.  
  
4.  Vyberte Service.asmx k otevření souboru v sadě Visual Studio.  
  
5.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
> [!NOTE]
>  Prvních pět kroků v tomto seznamu jsou volitelné. Modul runtime rozhraní .NET Framework, bude automaticky generovat webové služby první čas, kdy je požadována služba.  
  
> [!NOTE]
>  Následující kroky jsou nutné k vytvoření vzorku.  
  
1.  Otevřít [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] a přejděte do podadresáře \CS.  
  
2.  Klikněte pravým tlačítkem myši na ikonu podadresáři GenericsService a vyberte **sdílení a zabezpečení**.  
  
3.  V **sdílení na webu** vyberte **Sdílejte tuto složku**.  
  
> [!IMPORTANT]
>  Poznamenejte si název virtuálního adresáře, který je uvedený v **aliasy** podokně, protože jeho spuštění ukázky budete potřebovat.  
  
### <a name="to-build-the-sample-using-internet-information-services"></a>K vytvoření vzorku pomocí Internetové informační služby  
  
1.  Otevřete **Internetová informační služba** správy modulu snap-in a rozbalte **weby**.  
  
2.  Klepnutí levým tlačítkem myši **Default Web Site**, vyberte **nový**a potom vyberte **virtuální adresář?** vytvořit **Průvodce vytvořením virtuálního adresáře**.  
  
3.  Klikněte na tlačítko **Další**zadejte veřejný alias pro virtuální adresář a klikněte na tlačítko **Další**.  
  
4.  Zadejte cestu k adresáři, kam jste uložili ukázkové (obvykle podadresáři \CS\GenericsService) a klikněte na tlačítko **Další**. Klikněte na tlačítko **Další** ukončíte průvodce.  
  
> [!IMPORTANT]
>  Poznamenejte si název virtuálního adresáře, který je uvedený v **Alias** podokně, protože jeho spuštění ukázky budete potřebovat.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete okno prohlížeče a vyberte jeho adresa.  
  
2.  Typ  **http://localhost/[virtuální directory]/Service.asmx**, kde [virtuálního adresáře] představuje virtuální adresář, který jste vytvořili, když jste vytvořili vzorku.  
  
## <a name="remarks"></a>Poznámky  
 Ukázka zobrazí výchozí stránka technologie ASP.NET, která obsahuje odkazy na definice webové služby. Můžete přizpůsobit zobrazení kromě Změna zdrojového kódu webové služby. Další informace najdete v tématu [klienty vytváření XML webové služby](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 <xref:System.Web.Services>  
 <xref:System.Xml.Serialization>  
 [Serializace](../../../docs/standard/serialization/index.md)  
 [Webové služby XML vytvořený pomocí technologie ASP.NET a klienty webové služby XML](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)
