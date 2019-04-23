---
title: Více zabezpečený přístup k souborům a datům ve Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [Windows Forms], file access
- registry [Windows Forms]
- data access [Windows Forms]
- database access (Windows Forms security)
- data [Windows Forms], secure access
- file access [Windows Forms]
- security [Windows Forms], data access
ms.assetid: 3cd3e55b-2f5e-40dd-835d-f50f7ce08967
ms.openlocfilehash: 557c3296310a7eb3922a6c18b7b3de19ffac953c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115762"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a><span data-ttu-id="98682-102">Více zabezpečený přístup k souborům a datům ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98682-102">More Secure File and Data Access in Windows Forms</span></span>
<span data-ttu-id="98682-103">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Používá oprávnění k ochraně prostředkům a datům.</span><span class="sxs-lookup"><span data-stu-id="98682-103">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uses permissions to help protect resources and data.</span></span> <span data-ttu-id="98682-104">Pokud vaše aplikace může číst nebo zapisovat data závisí na oprávněních udělených aplikaci.</span><span class="sxs-lookup"><span data-stu-id="98682-104">Where your application can read or write data depends on the permissions granted to the application.</span></span> <span data-ttu-id="98682-105">Když aplikace běží v prostředí částečným vztahem důvěryhodnosti, možná nebudete mít přístup k datům nebo budete muset změnit způsob, jak přistupovat k datům.</span><span class="sxs-lookup"><span data-stu-id="98682-105">When your application runs in a partial trust environment, you might not have access to your data or you might have to change the way you access the data.</span></span>  
  
 <span data-ttu-id="98682-106">Pokud narazíte na omezení zabezpečení, máte dvě možnosti: uplatnit oprávnění (za předpokladu, že bylo uděleno pro vaši aplikaci) nebo verze operačního systému funkce napsané pro práci v částečném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="98682-106">When you encounter a security restriction, you have two options: assert the permission (assuming it has been granted to your application), or use a version of the feature written to work in partial trust.</span></span> <span data-ttu-id="98682-107">Následující části popisují, jak pracovat s souboru, database a přístup k registru z aplikací, které jsou spuštěny v prostředí s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="98682-107">The following sections discuss how to work with file, database, and registry access from applications that are running in a partial trust environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98682-108">Ve výchozím nastavení nástroje, které generují [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] nasazení ve výchozím nastavení tato nasazení žádající plné důvěryhodnosti z počítače, na kterých se používají.</span><span class="sxs-lookup"><span data-stu-id="98682-108">By default, tools that generate [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] deployments default these deployments to requesting Full Trust from the computers on which they run.</span></span> <span data-ttu-id="98682-109">Pokud chcete využít výhod vyššího zabezpečení spouštění v částečném vztahu důvěryhodnosti, je nutné změnit toto výchozí nastavení v sadě Visual Studio nebo jeden z [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] nástroje (Mage.exe nebo MageUI.exe).</span><span class="sxs-lookup"><span data-stu-id="98682-109">If you decide you want the added security benefits of running in partial trust, you must change this default in either Visual Studio or one of the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] tools (Mage.exe or MageUI.exe).</span></span> <span data-ttu-id="98682-110">Další informace o Windows Forms – zabezpečení a o tom, jak určit, příslušné úrovně důvěryhodnosti pro vaši aplikaci najdete v tématu [Přehled zabezpečení ve Windows Forms](security-in-windows-forms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="98682-110">For more information about Windows Forms security, and on how to determine the appropriate trust level for your application, see [Security in Windows Forms Overview](security-in-windows-forms-overview.md).</span></span>  
  
## <a name="file-access"></a><span data-ttu-id="98682-111">Přístup k souborům</span><span class="sxs-lookup"><span data-stu-id="98682-111">File Access</span></span>  
 <span data-ttu-id="98682-112"><xref:System.Security.Permissions.FileIOPermission> Třídy ovládacích prvků přístupu souborů a složek v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="98682-112">The <xref:System.Security.Permissions.FileIOPermission> class controls file and folder access in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="98682-113">Ve výchozím nastavení, systém zabezpečení nejsou udělena <xref:System.Security.Permissions.FileIOPermission> do prostředí částečným vztahem důvěryhodnosti, jako je místní intranet a Internet zóny.</span><span class="sxs-lookup"><span data-stu-id="98682-113">By default, the security system does not grant the <xref:System.Security.Permissions.FileIOPermission> to partial trust environments such as the local intranet and Internet zones.</span></span> <span data-ttu-id="98682-114">Aplikace, která vyžaduje přístup k souborům lze však i nadále fungovat v těchto prostředích je-li upravit návrh aplikace nebo použít různé metody pro přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="98682-114">However, an application that requires file access can still function in these environments if you modify the design of your application or use different methods to access files.</span></span> <span data-ttu-id="98682-115">Ve výchozím nastavení zóny místního intranetu je uděleno právo mít stejný přístup k serveru a stejný přístup adresáře pro připojení zpět k původnímu serveru a číst z jeho instalačního adresáře.</span><span class="sxs-lookup"><span data-stu-id="98682-115">By default, the local intranet zone is granted the right to have same site access and same directory access, to connect back to the site of its origin, and to read from its installation directory.</span></span> <span data-ttu-id="98682-116">Ve výchozím nastavení zóně Internet, je pouze uděleno právo na zpětné připojení k původnímu serveru.</span><span class="sxs-lookup"><span data-stu-id="98682-116">By default, the Internet zone, is only granted the right to connect back to the site of its origin.</span></span>  
  
### <a name="user-specified-files"></a><span data-ttu-id="98682-117">Soubory zadané uživatelem</span><span class="sxs-lookup"><span data-stu-id="98682-117">User-Specified Files</span></span>  
 <span data-ttu-id="98682-118">Jeden ze způsobů, jak zacházet s nemají přístup k souborům oprávnění je vyzvat uživatele k zadání určitých informací o souboru s použitím <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog> třídy.</span><span class="sxs-lookup"><span data-stu-id="98682-118">One way to deal with not having file access permission is to prompt the user to provide specific file information by using the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> class.</span></span> <span data-ttu-id="98682-119">Tato interakce uživatele pomáhá poskytovat některé záruku, že aplikace nelze speciálně načíst soukromé soubory nebo přepsat důležitých souborů.</span><span class="sxs-lookup"><span data-stu-id="98682-119">This user interaction helps provide some assurance that the application cannot maliciously load private files or overwrite important files.</span></span> <span data-ttu-id="98682-120"><xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> a <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody poskytují přístup čtení a zápis souboru otevřením souboru datového proudu souboru, který uživatel zadal.</span><span class="sxs-lookup"><span data-stu-id="98682-120">The <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> and <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> methods provide read and write file access by opening the file stream for the file that the user specified.</span></span> <span data-ttu-id="98682-121">Metody také pomáhají chránit uživatele souboru zakódováním cestě k souboru.</span><span class="sxs-lookup"><span data-stu-id="98682-121">The methods also help protect the user's file by obscuring the file's path.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98682-122">Tato oprávnění se liší v závislosti na tom, zda je vaše aplikace v zóně Internet nebo intranet.</span><span class="sxs-lookup"><span data-stu-id="98682-122">These permissions differ depending on whether your application is in the Internet zone or Intranet zone.</span></span> <span data-ttu-id="98682-123">Internetové zóně aplikace lze použít pouze <xref:System.Windows.Forms.OpenFileDialog>, že intranetové aplikace mít stejně neomezený souboru dialogové okno oprávnění.</span><span class="sxs-lookup"><span data-stu-id="98682-123">Internet zone applications can only use the <xref:System.Windows.Forms.OpenFileDialog>, whereas Intranet applications have unrestricted file dialog permission.</span></span>  
  
 <span data-ttu-id="98682-124"><xref:System.Security.Permissions.FileDialogPermission> Třída určuje, jaký typ dialogového okna souboru může vaše aplikace použít.</span><span class="sxs-lookup"><span data-stu-id="98682-124">The <xref:System.Security.Permissions.FileDialogPermission> class specifies what type of file dialog box your application can use.</span></span> <span data-ttu-id="98682-125">Následující tabulka uvádí hodnota musí mít použití každé <xref:System.Windows.Forms.FileDialog> třídy.</span><span class="sxs-lookup"><span data-stu-id="98682-125">The following table shows the value you must have to use each <xref:System.Windows.Forms.FileDialog> class.</span></span>  
  
|<span data-ttu-id="98682-126">Třída</span><span class="sxs-lookup"><span data-stu-id="98682-126">Class</span></span>|<span data-ttu-id="98682-127">Hodnota požadovaný přístup</span><span class="sxs-lookup"><span data-stu-id="98682-127">Required access value</span></span>|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
>  <span data-ttu-id="98682-128">Konkrétní oprávnění není požadována až <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> skutečně volání metody.</span><span class="sxs-lookup"><span data-stu-id="98682-128">The specific permission is not requested until the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is actually called.</span></span>  
  
 <span data-ttu-id="98682-129">Oprávnění k zobrazení dialogového okna souboru neuděluje vaše aplikace úplné přístup do všech členů <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, a <xref:System.Windows.Forms.SaveFileDialog> třídy.</span><span class="sxs-lookup"><span data-stu-id="98682-129">Permission to display a file dialog box does not grant your application full access to all members of the <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, and <xref:System.Windows.Forms.SaveFileDialog> classes.</span></span> <span data-ttu-id="98682-130">Konkrétní oprávnění, které je potřeba volat každou metodu, najdete v tématu referenční téma pro danou metodu v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] třídy dokumentaci ke knihovně.</span><span class="sxs-lookup"><span data-stu-id="98682-130">For the exact permissions that are required to call each method, see the reference topic for that method in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library documentation.</span></span>  
  
 <span data-ttu-id="98682-131">Následující příklad kódu používá <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metody k otevření souboru zadaného uživatelem do <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="98682-131">The following code example uses the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open a user-specified file into a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="98682-132">V příkladu vyžaduje <xref:System.Security.Permissions.FileDialogPermission> a přidružené <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="98682-132">The example requires <xref:System.Security.Permissions.FileDialogPermission> and the associated <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> enumeration value.</span></span> <span data-ttu-id="98682-133">Tento příklad ukazuje, jak zpracovat <xref:System.Security.SecurityException> k určení, zda uložit funkce by mělo být zakázáno.</span><span class="sxs-lookup"><span data-stu-id="98682-133">The example demonstrates how to handle the <xref:System.Security.SecurityException> to determine whether the save feature should be disabled.</span></span> <span data-ttu-id="98682-134">Tento příklad vyžaduje, aby vaše <xref:System.Windows.Forms.Form> má <xref:System.Windows.Forms.Button> ovládací prvek s názvem `ButtonOpen`a <xref:System.Windows.Forms.RichTextBox> ovládací prvek s názvem `RtfBoxMain`.</span><span class="sxs-lookup"><span data-stu-id="98682-134">This example requires that your <xref:System.Windows.Forms.Form> has a <xref:System.Windows.Forms.Button> control named `ButtonOpen`, and a <xref:System.Windows.Forms.RichTextBox> control named `RtfBoxMain`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98682-135">Programovou logiku pro uložení není funkce ukazuje příklad.</span><span class="sxs-lookup"><span data-stu-id="98682-135">The programming logic for the save feature is not shown in the example.</span></span>  
  
```vb  
Private Sub ButtonOpen_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles ButtonOpen.Click   
  
    Dim editingFileName as String = ""  
    Dim saveAllowed As Boolean = True  
  
    ' Displays the OpenFileDialog.  
    If (OpenFileDialog1.ShowDialog() = DialogResult.OK) Then  
        Dim userStream as System.IO.Stream  
        Try   
            ' Opens the file stream for the file selected by the user.  
            userStream =OpenFileDialog1.OpenFile()   
            Me.RtfBoxMain.LoadFile(userStream, _  
                RichTextBoxStreamType.PlainText)  
        Finally  
            userStream.Close()  
        End Try  
  
        ' Tries to get the file name selected by the user.  
        ' Failure means that the application does not have  
        ' unrestricted permission to the file.  
        Try   
            editingFileName = OpenFileDialog1.FileName  
        Catch ex As Exception  
            If TypeOf ex Is System.Security.SecurityException Then   
                ' The application does not have unrestricted permission   
                ' to the file so the save feature will be disabled.  
                saveAllowed = False   
            Else   
                Throw ex  
            End If  
        End Try  
    End If  
End Sub  
```  
  
```csharp  
private void ButtonOpen_Click(object sender, System.EventArgs e)   
{  
    String editingFileName = "";  
    Boolean saveAllowed = true;  
  
    // Displays the OpenFileDialog.  
    if (openFileDialog1.ShowDialog() == DialogResult.OK)   
    {  
        // Opens the file stream for the file selected by the user.  
        using (System.IO.Stream userStream = openFileDialog1.OpenFile())   
        {  
            this.RtfBoxMain.LoadFile(userStream,  
                RichTextBoxStreamType.PlainText);  
            userStream.Close();  
        }  
  
        // Tries to get the file name selected by the user.  
        // Failure means that the application does not have  
        // unrestricted permission to the file.  
        try   
        {  
            editingFileName = openFileDialog1.FileName;  
        }   
        catch (Exception ex)   
        {  
            if (ex is System.Security.SecurityException)   
            {  
                // The application does not have unrestricted permission   
                // to the file so the save feature will be disabled.  
                saveAllowed = false;   
            }   
            else   
            {  
                throw ex;  
            }  
        }  
    }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="98682-136">V jazyce Visual C#, ujistěte se, že přidáte kód pro povolení obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="98682-136">In Visual C#, ensure that you add code to enable the event handler.</span></span> <span data-ttu-id="98682-137">S použitím kódu z předchozího příkladu, následující kód ukazuje, jak povolit obslužné rutiny události.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span><span class="sxs-lookup"><span data-stu-id="98682-137">By using the code from the previous example, the following code shows how to enable the event handler.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span></span>  
  
### <a name="other-files"></a><span data-ttu-id="98682-138">Další soubory</span><span class="sxs-lookup"><span data-stu-id="98682-138">Other Files</span></span>  
 <span data-ttu-id="98682-139">Někdy můžete potřebovat pro čtení nebo zápis do souborů, že uživatel není zadán, například když musíte zachovat nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="98682-139">Sometimes you will need to read or write to files that the user does not specify, such as when you must persist application settings.</span></span> <span data-ttu-id="98682-140">V místní intranet a Internet zóny vaše aplikace nebude mít oprávnění k ukládání dat do místního souboru.</span><span class="sxs-lookup"><span data-stu-id="98682-140">In the local intranet and Internet zones, your application will not have permission to store data in a local file.</span></span> <span data-ttu-id="98682-141">Ale aplikace bude moct ukládání dat v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="98682-141">However, your application will be able to store data in isolated storage.</span></span> <span data-ttu-id="98682-142">Izolované úložiště je abstraktní datové přihrádky (nikoli specifickým umístěním úložiště), který obsahuje jeden nebo více souborů izolovaného úložiště nazývají "úložiště", které obsahují umístění skutečného adresáře, kde jsou uložená data.</span><span class="sxs-lookup"><span data-stu-id="98682-142">Isolated storage is an abstract data compartment (not a specific storage location) that contains one or more isolated storage files, called stores, that contain the actual directory locations where data is stored.</span></span> <span data-ttu-id="98682-143">Soubor přístupová oprávnění jako <xref:System.Security.Permissions.FileIOPermission> nejsou povinné; místo toho <xref:System.Security.Permissions.IsolatedStoragePermission> třídy řídí oprávnění pro izolované úložiště.</span><span class="sxs-lookup"><span data-stu-id="98682-143">File access permissions like <xref:System.Security.Permissions.FileIOPermission> are not required; instead, the <xref:System.Security.Permissions.IsolatedStoragePermission> class controls the permissions for isolated storage.</span></span> <span data-ttu-id="98682-144">Ve výchozím nastavení aplikace, které jsou spuštěny v místním intranetu a Internetu zóny může ukládat data pomocí izolované úložiště. nastavení, jako je disková kvóta se však může lišit.</span><span class="sxs-lookup"><span data-stu-id="98682-144">By default, applications that are running in the local intranet and Internet zones can store data using isolated storage; however, settings like disk quota can vary.</span></span> <span data-ttu-id="98682-145">Další informace o izolovaného úložiště naleznete v tématu [izolovaného úložiště](../../standard/io/isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="98682-145">For more information about isolated storage, see [Isolated Storage](../../standard/io/isolated-storage.md).</span></span>  
  
 <span data-ttu-id="98682-146">Následující příklad používá k zápisu dat do souboru, který je umístěn v úložišti izolovaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="98682-146">The following example uses isolated storage to write data to a file located in a store.</span></span> <span data-ttu-id="98682-147">V příkladu vyžaduje <xref:System.Security.Permissions.IsolatedStorageFilePermission> a <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="98682-147">The example requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> and the <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> enumeration value.</span></span> <span data-ttu-id="98682-148">Příklad ukazuje, čtení a zápis do určité hodnoty vlastností <xref:System.Windows.Forms.Button> ovládacího prvku do souboru v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="98682-148">The example demonstrates reading and writing certain property values of the <xref:System.Windows.Forms.Button> control to a file in isolated storage.</span></span> <span data-ttu-id="98682-149">`Read` Funkce by byla volána po spuštění aplikace a `Write` funkce by byla volána před ukončením aplikace.</span><span class="sxs-lookup"><span data-stu-id="98682-149">The `Read` function would be called after the application starts and the `Write` function would be called before the application ends.</span></span> <span data-ttu-id="98682-150">V příkladu vyžaduje, aby `Read` a `Write` funkce existovat jako členy <xref:System.Windows.Forms.Form> , která obsahuje <xref:System.Windows.Forms.Button> ovládací prvek s názvem `MainButton`.</span><span class="sxs-lookup"><span data-stu-id="98682-150">The example requires that the `Read` and `Write` functions exist as members of a <xref:System.Windows.Forms.Form> that contains a <xref:System.Windows.Forms.Button> control named `MainButton`.</span></span>  
  
```vb  
' Reads the button options from the isolated storage. Uses Default values   
' for the button if the options file does not exist.  
Public Sub Read()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try  
        ' Checks to see if the options.txt file exists.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
  
            ' Opens the file because it exists.  
            Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
                 (filename, IO.FileMode.Open,isoStore)  
            Dim reader as System.IO.StreamReader  
            Try   
                reader = new System.IO.StreamReader(isos)  
  
                ' Reads the values stored.  
                Dim converter As System.ComponentModel.TypeConverter  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Color))  
  
                Me.MainButton.BackColor = _   
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
                me.MainButton.ForeColor = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Font))  
                me.MainButton.Font = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Font)  
  
            Catch ex As Exception  
                Debug.WriteLine("Cannot read options " + _  
                    ex.ToString())  
            Finally  
                reader.Close()  
            End Try  
        End If  
  
    Catch ex As Exception  
        Debug.WriteLine("Cannot read options " + ex.ToString())  
    End Try  
End Sub  
  
' Writes the button options to the isolated storage.  
Public Sub Write()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try   
        ' Checks if the file exists, and if it does, tries to delete it.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
            isoStore.DeleteFile(filename)  
        End If  
    Catch ex As Exception  
        Debug.WriteLine("Cannot delete file " + ex.ToString())  
    End Try  
  
    ' Creates the options.txt file and writes the button options to it.  
    Dim writer as System.IO.StreamWriter  
    Try   
        Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
             (filename, IO.FileMode.CreateNew, isoStore)  
  
        writer = New System.IO.StreamWriter(isos)  
        Dim converter As System.ComponentModel.TypeConverter  
  
        converter = System.ComponentModel.TypeDescriptor.GetConverter _   
           (GetType(Color))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.BackColor))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.ForeColor))  
  
        converter = System.ComponentModel TypeDescriptor.GetConverter _   
           (GetType(Font))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.Font))  
  
    Catch ex as Exception  
        Debug.WriteLine("Cannot write options " + ex.ToString())  
  
    Finally  
        writer.Close()  
    End Try  
End Sub  
```  
  
```csharp  
// Reads the button options from the isolated storage. Uses default values   
// for the button if the options file does not exist.  
public void Read()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try  
    {  
        // Checks to see if the options.txt file exists.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            // Opens the file because it exists.  
            System.IO.IsolatedStorage.IsolatedStorageFileStream isos =   
                new System.IO.IsolatedStorage.IsolatedStorageFileStream  
                    (filename, System.IO.FileMode.Open,isoStore);  
            System.IO.StreamReader reader = null;  
            try   
            {  
                reader = new System.IO.StreamReader(isos);  
  
                // Reads the values stored.  
                TypeConverter converter ;  
                converter = TypeDescriptor.GetConverter(typeof(Color));  
  
                this.MainButton.BackColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
                this.MainButton.ForeColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
  
                converter = TypeDescriptor.GetConverter(typeof(Font));  
                this.MainButton.Font =   
                  (Font)(converter.ConvertFromString(reader.ReadLine()));  
            }  
            catch (Exception ex)  
            {   
                System.Diagnostics.Debug.WriteLine  
                     ("Cannot read options " + ex.ToString());  
            }  
            finally  
            {  
                reader.Close();  
            }  
        }  
    }   
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot read options " + ex.ToString());  
    }  
}  
  
// Writes the button options to the isolated storage.  
public void Write()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try   
    {  
        // Checks if the file exists and, if it does, tries to delete it.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            isoStore.DeleteFile(filename);  
        }  
    }  
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot delete file " + ex.ToString());  
    }  
  
    // Creates the options file and writes the button options to it.  
    System.IO.StreamWriter writer = null;  
    try   
    {  
        System.IO.IsolatedStorage.IsolatedStorageFileStream isos = new   
            System.IO.IsolatedStorage.IsolatedStorageFileStream(filename,   
            System.IO.FileMode.CreateNew,isoStore);  
  
        writer = new System.IO.StreamWriter(isos);  
        TypeConverter converter ;  
  
        converter = TypeDescriptor.GetConverter(typeof(Color));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.BackColor));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.ForeColor));  
  
        converter = TypeDescriptor.GetConverter(typeof(Font));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.Font));  
  
    }  
    catch (Exception ex)  
    {   
        System.Diagnostics.Debug.WriteLine  
           ("Cannot write options " + ex.ToString());  
    }  
    finally  
    {  
        writer.Close();  
    }  
}  
```  
  
## <a name="database-access"></a><span data-ttu-id="98682-151">Přístup k databázi</span><span class="sxs-lookup"><span data-stu-id="98682-151">Database Access</span></span>  
 <span data-ttu-id="98682-152">Oprávnění potřebná pro přístup k databázi se liší v závislosti na poskytovateli databáze; jenom aplikace, které jsou spuštěny s příslušnými oprávněními ale může přístup k databázi prostřednictvím datového připojení.</span><span class="sxs-lookup"><span data-stu-id="98682-152">The permissions required to access a database vary based on the database provider; however, only applications that are running with the appropriate permissions can access a database through a data connection.</span></span> <span data-ttu-id="98682-153">Další informace o oprávněních, které jsou nutné pro přístup k databázi, naleznete v tématu [zabezpečení přístupu kódu a ADO.NET](../data/adonet/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="98682-153">For more information about the permissions that are required to access a database, see [Code Access Security and ADO.NET](../data/adonet/code-access-security.md).</span></span>  
  
 <span data-ttu-id="98682-154">Pokud databáze nemůžete použít přímo, protože chcete, aby aplikace na spouštění v částečném vztahu důvěryhodnosti, můžete použít webovou službu, jako alternativu znamená, že přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="98682-154">If you cannot directly access a database because you want your application to run in partial trust, you can use a Web service as an alternative means to access your data.</span></span> <span data-ttu-id="98682-155">Webové služby je software, který můžete programově přistupovat přes síť.</span><span class="sxs-lookup"><span data-stu-id="98682-155">A Web service is a piece of software that can be programmatically accessed over a network.</span></span> <span data-ttu-id="98682-156">U webových služeb mohou aplikace sdílet data napříč zónami skupiny kódu.</span><span class="sxs-lookup"><span data-stu-id="98682-156">With Web services, applications can share data across code group zones.</span></span> <span data-ttu-id="98682-157">Ve výchozím nastavení aplikace v místním intranetu a Internetu zóny jsou udělena oprávnění k přístupu k jejich lokality původ, odkud můžou k volání webové služby hostované na stejném serveru.</span><span class="sxs-lookup"><span data-stu-id="98682-157">By default, applications in the local intranet and Internet zones are granted the right to access their sites of origin, which enables them to call a Web service hosted on the same server.</span></span> <span data-ttu-id="98682-158">Další informace najdete v části [webové služby v technologii ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) nebo [Windows Communication Foundation](../wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="98682-158">For more information see [Web Services in ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) or [Windows Communication Foundation](../wcf/index.md).</span></span>  
  
## <a name="registry-access"></a><span data-ttu-id="98682-159">Přístup k registru</span><span class="sxs-lookup"><span data-stu-id="98682-159">Registry Access</span></span>  
 <span data-ttu-id="98682-160"><xref:System.Security.Permissions.RegistryPermission> Třídy řídí přístup k registru operačního systému.</span><span class="sxs-lookup"><span data-stu-id="98682-160">The <xref:System.Security.Permissions.RegistryPermission> class controls access to the operating system registry.</span></span> <span data-ttu-id="98682-161">Ve výchozím nastavení můžete pouze aplikace, které jsou spuštěné místně přístup k registru.</span><span class="sxs-lookup"><span data-stu-id="98682-161">By default, only applications that are running locally can access the registry.</span></span>  <span data-ttu-id="98682-162"><xref:System.Security.Permissions.RegistryPermission> uděluje jenom aplikace právo zkuste přístup k registru; to nezaručuje, že přístup bude úspěšné, protože operační systém stále vynucuje zabezpečení v registru.</span><span class="sxs-lookup"><span data-stu-id="98682-162"><xref:System.Security.Permissions.RegistryPermission> only grants an application the right to try registry access; it does not guarantee access will succeed, because the operating system still enforces security on the registry.</span></span>  
  
 <span data-ttu-id="98682-163">Protože nelze získat přístup k registru v částečném vztahu důvěryhodnosti, budete muset najít jiné metody ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="98682-163">Because you cannot access the registry under partial trust, you may need to find other methods of storing your data.</span></span> <span data-ttu-id="98682-164">Při ukládání nastavení aplikace používání izolovaného úložiště namísto registru.</span><span class="sxs-lookup"><span data-stu-id="98682-164">When you store application settings, use isolated storage instead of the registry.</span></span> <span data-ttu-id="98682-165">Izolované úložiště lze také ukládat další soubory specifické pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="98682-165">Isolated storage can also be used to store other application-specific files.</span></span> <span data-ttu-id="98682-166">Můžete také ukládat informace o globální aplikace o server nebo server původu, protože ve výchozím nastavení aplikace jsou udělena oprávnění k přístupu k původnímu serveru.</span><span class="sxs-lookup"><span data-stu-id="98682-166">You can also store global application information about the server or site of origin, because by default an application is granted the right to access the site of its origin.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98682-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98682-167">See also</span></span>

- [<span data-ttu-id="98682-168">Zabezpečenější tisk ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98682-168">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)
- [<span data-ttu-id="98682-169">Dodatečné informace o zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98682-169">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)
- [<span data-ttu-id="98682-170">Přehled zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98682-170">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)
- [<span data-ttu-id="98682-171">Windows Forms – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="98682-171">Windows Forms Security</span></span>](windows-forms-security.md)
- [<span data-ttu-id="98682-172">Mage.exe (Manifest Generation and Editing Tool)</span><span class="sxs-lookup"><span data-stu-id="98682-172">Mage.exe (Manifest Generation and Editing Tool)</span></span>](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [<span data-ttu-id="98682-173">MageUI.exe (Manifest Generation and Editing Tool, grafický klient)</span><span class="sxs-lookup"><span data-stu-id="98682-173">MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)</span></span>](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
