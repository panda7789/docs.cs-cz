---
title: Bezpečnější přístup k souborům a datům
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
ms.openlocfilehash: a29c2f7137440e64fbf8095f77d5d10d0505bc2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185902"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a><span data-ttu-id="aab16-102">Více zabezpečený přístup k souborům a datům ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aab16-102">More Secure File and Data Access in Windows Forms</span></span>
<span data-ttu-id="aab16-103">Rozhraní .NET Framework používá oprávnění k ochraně prostředků a dat.</span><span class="sxs-lookup"><span data-stu-id="aab16-103">The .NET Framework uses permissions to help protect resources and data.</span></span> <span data-ttu-id="aab16-104">Kde vaše aplikace může číst nebo zapisovat data závisí na oprávnění udělených aplikaci.</span><span class="sxs-lookup"><span data-stu-id="aab16-104">Where your application can read or write data depends on the permissions granted to the application.</span></span> <span data-ttu-id="aab16-105">Při spuštění aplikace v prostředí částečné důvěryhodnosti, pravděpodobně nemáte přístup k datům nebo budete muset změnit způsob přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="aab16-105">When your application runs in a partial trust environment, you might not have access to your data or you might have to change the way you access the data.</span></span>  
  
 <span data-ttu-id="aab16-106">Pokud narazíte na omezení zabezpečení, máte dvě možnosti: uplatnit oprávnění (za předpokladu, že byla udělena vaší aplikaci) nebo použít verzi funkce napsané pro práci v částečném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="aab16-106">When you encounter a security restriction, you have two options: assert the permission (assuming it has been granted to your application), or use a version of the feature written to work in partial trust.</span></span> <span data-ttu-id="aab16-107">Následující části popisují, jak pracovat s přístupem k souborům, databázím a registru z aplikací spuštěných v prostředí s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="aab16-107">The following sections discuss how to work with file, database, and registry access from applications that are running in a partial trust environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aab16-108">Ve výchozím nastavení nástroje, které generují nasazení ClickOnce, ve výchozím nastavení tato nasazení požadují úplné důvěryhodnosti z počítačů, ve kterých jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="aab16-108">By default, tools that generate ClickOnce deployments default these deployments to requesting Full Trust from the computers on which they run.</span></span> <span data-ttu-id="aab16-109">Pokud se rozhodnete, že chcete přidat výhody zabezpečení spuštění v částečném vztahu důvěryhodnosti, musíte změnit toto výchozí nastavení v sadě Visual Studio nebo v jednom z nástrojů sady Windows SDK (Mage.exe nebo MageUI.exe).</span><span class="sxs-lookup"><span data-stu-id="aab16-109">If you decide you want the added security benefits of running in partial trust, you must change this default in either Visual Studio or one of the Windows SDK tools (Mage.exe or MageUI.exe).</span></span> <span data-ttu-id="aab16-110">Další informace o zabezpečení formulářů Windows Forms a o určení odpovídající úrovně důvěryhodnosti aplikace naleznete [v tématu Zabezpečení v Přehledu formulářů systému Windows](security-in-windows-forms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="aab16-110">For more information about Windows Forms security, and on how to determine the appropriate trust level for your application, see [Security in Windows Forms Overview](security-in-windows-forms-overview.md).</span></span>  
  
## <a name="file-access"></a><span data-ttu-id="aab16-111">Přístup k souborům</span><span class="sxs-lookup"><span data-stu-id="aab16-111">File Access</span></span>  
 <span data-ttu-id="aab16-112">Třída <xref:System.Security.Permissions.FileIOPermission> řídí přístup k souborům a složkám v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aab16-112">The <xref:System.Security.Permissions.FileIOPermission> class controls file and folder access in the .NET Framework.</span></span> <span data-ttu-id="aab16-113">Ve výchozím nastavení systém zabezpečení <xref:System.Security.Permissions.FileIOPermission> neuděluje prostředí částečné důvěryhodnosti, jako je například místní intranet a internetové zóny.</span><span class="sxs-lookup"><span data-stu-id="aab16-113">By default, the security system does not grant the <xref:System.Security.Permissions.FileIOPermission> to partial trust environments such as the local intranet and Internet zones.</span></span> <span data-ttu-id="aab16-114">Aplikace, která vyžaduje přístup k souborům, však může v těchto prostředích stále fungovat, pokud změníte návrh aplikace nebo pro přístup k souborům použijete různé metody.</span><span class="sxs-lookup"><span data-stu-id="aab16-114">However, an application that requires file access can still function in these environments if you modify the design of your application or use different methods to access files.</span></span> <span data-ttu-id="aab16-115">Ve výchozím nastavení je místní intranetové zóně uděleno právo mít stejný přístup k webu a stejný přístup k adresáři, připojit se zpět k webu svého původu a číst z instalačního adresáře.</span><span class="sxs-lookup"><span data-stu-id="aab16-115">By default, the local intranet zone is granted the right to have same site access and same directory access, to connect back to the site of its origin, and to read from its installation directory.</span></span> <span data-ttu-id="aab16-116">Ve výchozím nastavení je internetové zóně uděleno pouze právo připojit se zpět k místu, kde je původ.</span><span class="sxs-lookup"><span data-stu-id="aab16-116">By default, the Internet zone, is only granted the right to connect back to the site of its origin.</span></span>  
  
### <a name="user-specified-files"></a><span data-ttu-id="aab16-117">Soubory zadané uživatelem</span><span class="sxs-lookup"><span data-stu-id="aab16-117">User-Specified Files</span></span>  
 <span data-ttu-id="aab16-118">Jedním ze způsobů, jak se vypořádat s tím, že nemáte <xref:System.Windows.Forms.OpenFileDialog> oprávnění <xref:System.Windows.Forms.SaveFileDialog> k přístupu k souborům, je vyzvat uživatele k zadání konkrétních informací o souboru pomocí třídy nebo.</span><span class="sxs-lookup"><span data-stu-id="aab16-118">One way to deal with not having file access permission is to prompt the user to provide specific file information by using the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> class.</span></span> <span data-ttu-id="aab16-119">Tato interakce s uživatelem pomáhá poskytnout určitou jistotu, že aplikace nemůže zlomyslně načíst soukromé soubory nebo přepsat důležité soubory.</span><span class="sxs-lookup"><span data-stu-id="aab16-119">This user interaction helps provide some assurance that the application cannot maliciously load private files or overwrite important files.</span></span> <span data-ttu-id="aab16-120">Metody <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> a poskytují přístup k souborům pro čtení a zápis otevřením datového proudu souboru pro soubor, který uživatel zadal.</span><span class="sxs-lookup"><span data-stu-id="aab16-120">The <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> and <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> methods provide read and write file access by opening the file stream for the file that the user specified.</span></span> <span data-ttu-id="aab16-121">Metody také pomáhají chránit soubor uživatele tím, že zakrývají cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="aab16-121">The methods also help protect the user's file by obscuring the file's path.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aab16-122">Tato oprávnění se liší v závislosti na tom, zda je aplikace v zóně Internet nebo Intranet.</span><span class="sxs-lookup"><span data-stu-id="aab16-122">These permissions differ depending on whether your application is in the Internet zone or Intranet zone.</span></span> <span data-ttu-id="aab16-123">Aplikace zóny Internetu mohou <xref:System.Windows.Forms.OpenFileDialog>používat pouze aplikace , zatímco aplikace intranetu mají oprávnění k dialogovému oknu bez omezení.</span><span class="sxs-lookup"><span data-stu-id="aab16-123">Internet zone applications can only use the <xref:System.Windows.Forms.OpenFileDialog>, whereas Intranet applications have unrestricted file dialog permission.</span></span>  
  
 <span data-ttu-id="aab16-124">Třída <xref:System.Security.Permissions.FileDialogPermission> určuje, jaký typ dialogového okna souboru může aplikace použít.</span><span class="sxs-lookup"><span data-stu-id="aab16-124">The <xref:System.Security.Permissions.FileDialogPermission> class specifies what type of file dialog box your application can use.</span></span> <span data-ttu-id="aab16-125">V následující tabulce je uvedena hodnota, <xref:System.Windows.Forms.FileDialog> kterou musíte použít pro každou třídu.</span><span class="sxs-lookup"><span data-stu-id="aab16-125">The following table shows the value you must have to use each <xref:System.Windows.Forms.FileDialog> class.</span></span>  
  
|<span data-ttu-id="aab16-126">Třída</span><span class="sxs-lookup"><span data-stu-id="aab16-126">Class</span></span>|<span data-ttu-id="aab16-127">Požadovaná hodnota přístupu</span><span class="sxs-lookup"><span data-stu-id="aab16-127">Required access value</span></span>|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
> <span data-ttu-id="aab16-128">Konkrétní oprávnění není požadováno, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> dokud je metoda skutečně volána.</span><span class="sxs-lookup"><span data-stu-id="aab16-128">The specific permission is not requested until the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is actually called.</span></span>  
  
 <span data-ttu-id="aab16-129">Oprávnění k zobrazení dialogového okna souboru neuděluje aplikaci <xref:System.Windows.Forms.FileDialog> <xref:System.Windows.Forms.OpenFileDialog>úplný <xref:System.Windows.Forms.SaveFileDialog> přístup všem členům tříd , a tříd.</span><span class="sxs-lookup"><span data-stu-id="aab16-129">Permission to display a file dialog box does not grant your application full access to all members of the <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, and <xref:System.Windows.Forms.SaveFileDialog> classes.</span></span> <span data-ttu-id="aab16-130">Přesná oprávnění, která jsou vyžadována pro volání jednotlivých metod, naleznete v referenčním tématu pro tuto metodu v dokumentaci ke knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aab16-130">For the exact permissions that are required to call each method, see the reference topic for that method in the .NET Framework class library documentation.</span></span>  
  
 <span data-ttu-id="aab16-131">Následující příklad kódu <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> používá metodu k otevření souboru zadaného uživatelem do ovládacího <xref:System.Windows.Forms.RichTextBox> prvku.</span><span class="sxs-lookup"><span data-stu-id="aab16-131">The following code example uses the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open a user-specified file into a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="aab16-132">Příklad vyžaduje <xref:System.Security.Permissions.FileDialogPermission> a <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> související výčtu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="aab16-132">The example requires <xref:System.Security.Permissions.FileDialogPermission> and the associated <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> enumeration value.</span></span> <span data-ttu-id="aab16-133">Příklad ukazuje, jak zpracovat <xref:System.Security.SecurityException> určit, zda má být zakázána funkce ukládání.</span><span class="sxs-lookup"><span data-stu-id="aab16-133">The example demonstrates how to handle the <xref:System.Security.SecurityException> to determine whether the save feature should be disabled.</span></span> <span data-ttu-id="aab16-134">Tento příklad vyžaduje, <xref:System.Windows.Forms.Button> aby `ButtonOpen`váš <xref:System.Windows.Forms.Form> má <xref:System.Windows.Forms.RichTextBox> ovládací `RtfBoxMain`prvek s názvem a ovládací prvek s názvem .</span><span class="sxs-lookup"><span data-stu-id="aab16-134">This example requires that your <xref:System.Windows.Forms.Form> has a <xref:System.Windows.Forms.Button> control named `ButtonOpen`, and a <xref:System.Windows.Forms.RichTextBox> control named `RtfBoxMain`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aab16-135">Programovací logika pro funkci uložení není uvedena v příkladu.</span><span class="sxs-lookup"><span data-stu-id="aab16-135">The programming logic for the save feature is not shown in the example.</span></span>  
  
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
> <span data-ttu-id="aab16-136">V jazyce Visual C# se ujistěte, že přidáte kód pro povolení obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="aab16-136">In Visual C#, ensure that you add code to enable the event handler.</span></span> <span data-ttu-id="aab16-137">Pomocí kódu z předchozího příkladu následující kód ukazuje, jak povolit obslužnou rutinu události.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span><span class="sxs-lookup"><span data-stu-id="aab16-137">By using the code from the previous example, the following code shows how to enable the event handler.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span></span>  
  
### <a name="other-files"></a><span data-ttu-id="aab16-138">Další soubory</span><span class="sxs-lookup"><span data-stu-id="aab16-138">Other Files</span></span>  
 <span data-ttu-id="aab16-139">Někdy budete muset číst nebo zapisovat do souborů, které uživatel nezadá, například když je nutné zachovat nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="aab16-139">Sometimes you will need to read or write to files that the user does not specify, such as when you must persist application settings.</span></span> <span data-ttu-id="aab16-140">V místních intranetových a internetových zónách nebude mít aplikace oprávnění k ukládání dat do místního souboru.</span><span class="sxs-lookup"><span data-stu-id="aab16-140">In the local intranet and Internet zones, your application will not have permission to store data in a local file.</span></span> <span data-ttu-id="aab16-141">Vaše aplikace však bude moci ukládat data v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="aab16-141">However, your application will be able to store data in isolated storage.</span></span> <span data-ttu-id="aab16-142">Izolované úložiště je abstraktní datový oddíl (nikoli konkrétní umístění úložiště), který obsahuje jeden nebo více izolovaných souborů úložiště, nazývaných úložiště, které obsahují skutečná umístění adresářů, kde jsou uložena data.</span><span class="sxs-lookup"><span data-stu-id="aab16-142">Isolated storage is an abstract data compartment (not a specific storage location) that contains one or more isolated storage files, called stores, that contain the actual directory locations where data is stored.</span></span> <span data-ttu-id="aab16-143">Oprávnění pro <xref:System.Security.Permissions.FileIOPermission> přístup k souborům nejsou vyžadována. místo toho <xref:System.Security.Permissions.IsolatedStoragePermission> třída řídí oprávnění pro izolované úložiště.</span><span class="sxs-lookup"><span data-stu-id="aab16-143">File access permissions like <xref:System.Security.Permissions.FileIOPermission> are not required; instead, the <xref:System.Security.Permissions.IsolatedStoragePermission> class controls the permissions for isolated storage.</span></span> <span data-ttu-id="aab16-144">Ve výchozím nastavení mohou aplikace spuštěné v místních intranetových a internetových zónách ukládat data pomocí izolovaného úložiště. Nastavení, jako je disková kvóta, se však mohou lišit.</span><span class="sxs-lookup"><span data-stu-id="aab16-144">By default, applications that are running in the local intranet and Internet zones can store data using isolated storage; however, settings like disk quota can vary.</span></span> <span data-ttu-id="aab16-145">Další informace o izolovaném úložišti naleznete v [tématu Izolované úložiště](../../standard/io/isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="aab16-145">For more information about isolated storage, see [Isolated Storage](../../standard/io/isolated-storage.md).</span></span>  
  
 <span data-ttu-id="aab16-146">Následující příklad používá izolované úložiště k zápisu dat do souboru umístěného v úložišti.</span><span class="sxs-lookup"><span data-stu-id="aab16-146">The following example uses isolated storage to write data to a file located in a store.</span></span> <span data-ttu-id="aab16-147">Příklad vyžaduje <xref:System.Security.Permissions.IsolatedStorageFilePermission> a <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> hodnotu výčtu.</span><span class="sxs-lookup"><span data-stu-id="aab16-147">The example requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> and the <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> enumeration value.</span></span> <span data-ttu-id="aab16-148">Příklad ukazuje čtení a zápis určitých <xref:System.Windows.Forms.Button> hodnot vlastností ovládacího prvku do souboru v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="aab16-148">The example demonstrates reading and writing certain property values of the <xref:System.Windows.Forms.Button> control to a file in isolated storage.</span></span> <span data-ttu-id="aab16-149">Funkce `Read` bude volána po spuštění `Write` aplikace a funkce bude volána před ukončením aplikace.</span><span class="sxs-lookup"><span data-stu-id="aab16-149">The `Read` function would be called after the application starts and the `Write` function would be called before the application ends.</span></span> <span data-ttu-id="aab16-150">Příklad vyžaduje, `Read` aby `Write` funkce a existovaly jako <xref:System.Windows.Forms.Button> členové `MainButton`ovládacího <xref:System.Windows.Forms.Form> prvku, který obsahuje ovládací prvek s názvem .</span><span class="sxs-lookup"><span data-stu-id="aab16-150">The example requires that the `Read` and `Write` functions exist as members of a <xref:System.Windows.Forms.Form> that contains a <xref:System.Windows.Forms.Button> control named `MainButton`.</span></span>  
  
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
  
## <a name="database-access"></a><span data-ttu-id="aab16-151">Přístup k databázi</span><span class="sxs-lookup"><span data-stu-id="aab16-151">Database Access</span></span>  
 <span data-ttu-id="aab16-152">Oprávnění požadovaná pro přístup k databázi se liší v závislosti na poskytovateli databáze. pouze aplikace, které jsou spuštěny s příslušnými oprávněními, však mohou přistupovat k databázi prostřednictvím datového připojení.</span><span class="sxs-lookup"><span data-stu-id="aab16-152">The permissions required to access a database vary based on the database provider; however, only applications that are running with the appropriate permissions can access a database through a data connection.</span></span> <span data-ttu-id="aab16-153">Další informace o oprávněních, která jsou vyžadována pro přístup k databázi, naleznete v [tématu Zabezpečení přístupu kódu a ADO.NET](../data/adonet/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="aab16-153">For more information about the permissions that are required to access a database, see [Code Access Security and ADO.NET](../data/adonet/code-access-security.md).</span></span>  
  
 <span data-ttu-id="aab16-154">Pokud nelze přímo přistupovat k databázi, protože chcete, aby aplikace spustit v částečném vztahu důvěryhodnosti, můžete použít webovou službu jako alternativní prostředek pro přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="aab16-154">If you cannot directly access a database because you want your application to run in partial trust, you can use a Web service as an alternative means to access your data.</span></span> <span data-ttu-id="aab16-155">Webová služba je software, ke kterému lze programově přistupovat prostředně prostředně.</span><span class="sxs-lookup"><span data-stu-id="aab16-155">A Web service is a piece of software that can be programmatically accessed over a network.</span></span> <span data-ttu-id="aab16-156">Pomocí webových služeb mohou aplikace sdílet data mezi zónami kódových skupin.</span><span class="sxs-lookup"><span data-stu-id="aab16-156">With Web services, applications can share data across code group zones.</span></span> <span data-ttu-id="aab16-157">Ve výchozím nastavení je aplikacím v místní chu-intranetu a internetových zónách uděleno právo na přístup k jejich webům původu, což jim umožňuje volat webovou službu hostovanou na stejném serveru.</span><span class="sxs-lookup"><span data-stu-id="aab16-157">By default, applications in the local intranet and Internet zones are granted the right to access their sites of origin, which enables them to call a Web service hosted on the same server.</span></span> <span data-ttu-id="aab16-158">Další informace naleznete [v tématu Webové služby v ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) nebo Windows Communication [Foundation](../wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="aab16-158">For more information see [Web Services in ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) or [Windows Communication Foundation](../wcf/index.md).</span></span>  
  
## <a name="registry-access"></a><span data-ttu-id="aab16-159">Přístup k registru</span><span class="sxs-lookup"><span data-stu-id="aab16-159">Registry Access</span></span>  
 <span data-ttu-id="aab16-160">Třída <xref:System.Security.Permissions.RegistryPermission> řídí přístup k registru operačního systému.</span><span class="sxs-lookup"><span data-stu-id="aab16-160">The <xref:System.Security.Permissions.RegistryPermission> class controls access to the operating system registry.</span></span> <span data-ttu-id="aab16-161">Ve výchozím nastavení mohou k registru přistupovat pouze aplikace, které jsou spuštěny místně.</span><span class="sxs-lookup"><span data-stu-id="aab16-161">By default, only applications that are running locally can access the registry.</span></span>  <span data-ttu-id="aab16-162"><xref:System.Security.Permissions.RegistryPermission>pouze uděluje aplikaci právo vyzkoušet přístup k registru; nezaručuje, že přístup bude úspěšný, protože operační systém stále vynucuje zabezpečení v registru.</span><span class="sxs-lookup"><span data-stu-id="aab16-162"><xref:System.Security.Permissions.RegistryPermission> only grants an application the right to try registry access; it does not guarantee access will succeed, because the operating system still enforces security on the registry.</span></span>  
  
 <span data-ttu-id="aab16-163">Vzhledem k tomu, že nelze získat přístup k registru pod částečným vztahem důvěryhodnosti, bude pravděpodobně nutné najít jiné metody ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="aab16-163">Because you cannot access the registry under partial trust, you may need to find other methods of storing your data.</span></span> <span data-ttu-id="aab16-164">Při ukládání nastavení aplikace použijte místo registru izolované úložiště.</span><span class="sxs-lookup"><span data-stu-id="aab16-164">When you store application settings, use isolated storage instead of the registry.</span></span> <span data-ttu-id="aab16-165">Izolované úložiště lze také použít k ukládání jiných souborů specifických pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="aab16-165">Isolated storage can also be used to store other application-specific files.</span></span> <span data-ttu-id="aab16-166">Můžete také ukládat informace o globální aplikaci o serveru nebo webu původu, protože ve výchozím nastavení je aplikaci uděleno právo na přístup k webu svého původu.</span><span class="sxs-lookup"><span data-stu-id="aab16-166">You can also store global application information about the server or site of origin, because by default an application is granted the right to access the site of its origin.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aab16-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="aab16-167">See also</span></span>

- [<span data-ttu-id="aab16-168">Bezpečnější tisk ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aab16-168">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)
- [<span data-ttu-id="aab16-169">Dodatečné informace o zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aab16-169">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)
- [<span data-ttu-id="aab16-170">Přehled zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aab16-170">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)
- [<span data-ttu-id="aab16-171">Windows Forms – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="aab16-171">Windows Forms Security</span></span>](windows-forms-security.md)
- [<span data-ttu-id="aab16-172">Mage.exe (Manifest Generation and Editing Tool)</span><span class="sxs-lookup"><span data-stu-id="aab16-172">Mage.exe (Manifest Generation and Editing Tool)</span></span>](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [<span data-ttu-id="aab16-173">MageUI.exe (Manifest Generation and Editing Tool, grafický klient)</span><span class="sxs-lookup"><span data-stu-id="aab16-173">MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)</span></span>](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
