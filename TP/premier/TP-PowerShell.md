# TP-PowerShell

### 📅 Date : 29/03/2025

### 👨‍🎓 Nom : Guinand Yulian

### 🎓 Formation : BTS SIO Alt (Option SLAM)

### 🏫 Établissement : Pasteur Mont-Roland (Dole)

### 👨‍🏫 Enseignant : Mr Kyllian Bletrix

## 🔍 **Objectif du Travail Pratique**

Ce travail pratique a pour but d’initier à **PowerShell** à travers différentes manipulations et commandes essentielles. Nous avons abordé les aspects suivants :

1. **Obtenir de l’aide sur une commande** – Utilisation des commandes d’aide pour comprendre le fonctionnement des cmdlets.
2. **Gérer les fichiers et les dossiers** – Manipulations de base pour créer, modifier et supprimer des fichiers et dossiers.
3. **Accès aux propriétés et aux méthodes d’un objet** – Comprendre et exploiter les objets PowerShell.
4. **Le monitoring** – Surveillance des ressources et processus système.
5. **Les services** – Gestion des services Windows avec PowerShell.
6. **Structuration de fichiers** – Organisation et manipulation avancée des fichiers.

## 📜 **Sommaire**

1. **Exerice 1** : Obtenir de l'aide sur une commande
2. **Exercice 2** : Gerer les fichiers et les dossiers
3. **Exercice 3** : Acces aux proprietes et aux methodes d'un objet
4. **Exerice 4** : Monitoring
5. **Exercice 5** : Les Services
6. **Exercice 6** : Archive structuree

---

## Exercice 1 : Obtenir de l'aide sur une commande

### 1) Afficher l'aide sur la commande Get-Alias

Commande :

```powershell
Get-Help Get-Alias
```

Retour :

```powershell
NOM
    Get-Alias

SYNTAXE
    Get-Alias [[-Name] <string[]>]  [<CommonParameters>]

    Get-Alias  [<CommonParameters>]


ALIAS
    gal


REMARQUES
    Get-Help ne parvient pas à trouver les fichiers d’aide de cette applet de commande sur cet ordinateur. Il ne trouve qu’une aide partielle.
        -- Pour telecharger et installer les fichiers d’aide du module comportant cette applet de commande, utilisez Update-Help.
        -- Pour afficher en ligne la rubrique d’aide de cette applet de commande, tapez : « Get-Help Get-Alias -Online » ou
           accedez à https://go.microsoft.com/fwlink/?LinkID=113306.
```

### 2) Afficher tous les alias dont le nom commence par la lettre w

Commande :

```powershell
Get-Alias -Name w*
```

Retour :

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           wget -> Invoke-WebRequest
Alias           where -> Where-Object
Alias           wjb -> Wait-Job
Alias           write -> Write-Output
Alias           Write-FileSystemCache                              2.0.0.0    Storage
```

### 3) Afficher la commande qui correspond à l’alias dont le nom est sl

Commande :

```powershell
Get-Alias -Name sl
```

Retour :

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           sl -> Set-Location
```

### 4) Afficher tous les alias dont la definition est Get-Childitem

Commande :

```powershell
Get-Alias -Definition Get-ChildItem
```

Retour :

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

### 5) Afficher les methodes et les proprietes des objets retournes par la commande Get-Location

Commande :

```powershell
Get-Location | Get-Member
```

Retour :

```powershell
   TypeName : System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

### 6) Afficher les methodes et les proprietes des objets retournes par la commande Get-PSDrive

Commande :

```powershell
Get-PSDrive | Get-Member
```

Retour :

```powershell
   TypeName : System.Management.Automation.PSDriveInfo

Name            MemberType     Definition
----            ----------     ----------
CompareTo       Method         int CompareTo(System.Management.Automation.PSDriveInfo drive), int CompareTo(System.Object obj), int IComparable.CompareTo(System.Object obj)
Equals          Method         bool Equals(System.Object obj), bool Equals(System.Management.Automation.PSDriveInfo drive)
GetHashCode     Method         int GetHashCode()
GetType         Method         type GetType()
ToString        Method         string ToString()
Credential      Property       pscredential Credential {get;}
CurrentLocation Property       string CurrentLocation {get;set;}
Description     Property       string Description {get;set;}
DisplayRoot     Property       string DisplayRoot {get;}
MaximumSize     Property       System.Nullable[long] MaximumSize {get;}
Name            Property       string Name {get;}
Provider        Property       System.Management.Automation.ProviderInfo Provider {get;}
Root            Property       string Root {get;}
Free            ScriptProperty System.Object Free {get=## Ensure that this is a FileSystem drive...
Used            ScriptProperty System.Object Used {get=## Ensure that this is a FileSystem drive...
```

## Exercice 2 : Gerer les fichiers et les dossiers

### 1) Afficher le chemin du dossier courant

Commande :

```powershell
Get-Location
```

Retour :

```powershell
Path
----
C:\Users\yulia
```

### 2) Se deplacer à la racine de la partition C

Commande :

```powershell
Set-Location C:\
```

Dans le terminal de commande :

```powershell
PS C:\
```

### 3) Afficher la liste des dossiers et des fichiers

Commande :

```powershell
Get-ChildItem
```

Retour :

```powershell
    Repertoire : C:\


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        28/12/2024     16:25                AMD
d-----        31/12/2024     13:17                NVIDIA
d-----        07/12/2019     10:14                PerfLogs
d-----        29/01/2025     21:48                php-8.4.3
d-r---        29/03/2025     13:58                Program Files
d-r---        15/03/2025     12:28                Program Files (x86)
d-----        28/12/2024     17:56                Riot Games
d-r---        28/12/2024     14:51                Users
d-----        16/03/2025     23:38                Windows
d-----        29/01/2025     21:56                xampp
d-----        30/12/2024     23:03                XboxGames
```

### 4) Creer un dossier test PowerShell à cet emplacement

Commande :

```powershell
New-Item -ItemType Directory -Name test
```

Retour :

```powershell
    Repertoire : C:\


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        29/03/2025     16:48                test
```

### 5) Se deplacer dans ce dossier

Commande :

```powershell
Set-Location C:\test
```

Dans le terminal de commande :

```powershell
PS C:\test>
```

### 6) Creer un dossier "testdossier"

Commande :

```powershell
New-Item -ItemType Directory -Name testdossier
```

Retour :

```powershell
    Repertoire : C:\test


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        29/03/2025     16:56                testdossier
```

### 7) Creer un fichier nomme test1.txt, contenanant la phrase " Tp Powershell 1 "

Commande :

```powershell
New-Item -ItemType File -Name test1.txt -Value "Tp Powershell 1"
```

Retour :

```powershell
    Repertoire : C:\test


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        29/03/2025     18:02             15 test1.txt
```

### 8) Afficher la liste des dossiers et des fichiers

Commande :

```powershell
Get-ChildItem
```

Retour :

```powershell
    Repertoire : C:\test


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        29/03/2025     16:56                testdossier
```

### 9) Copier le fichier test1.txt sous le nom test2.txt

Commande :

```powershell
Copy-Item test1.txt test2.txt
```

Retour :

```powershell
PS C:\test> Copy-Item test1.txt test2.txt

PS C:\test> Get-ChildItem


    Repertoire : C:\test


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        29/03/2025     16:56                testdossier
-a----        29/03/2025     18:02             15 test1.txt
-a----        29/03/2025     18:02             15 test2.txt
```

### 10) Renommer le fichier tes1.txt sous le nom essai1.txt

Commande :

```powershell
Rename-Item .\test1.txt .\essai1.txt
```

Retour :

```powershell
PS C:\test> Rename-Item .\test1.txt .\essai1.txt

PS C:\test> Get-ChildItem


    Repertoire : C:\test


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        29/03/2025     16:56                testdossier
-a----        29/03/2025     18:02             15 essai1.txt
-a----        29/03/2025     18:02             15 test2.txt
```

### Copier le fichier essai1.txt dans le dossier testdossier

Commande :

```powershell
Copy-Item -Path .\essai1.txt -Destination .\testdossier\
```

Retour :

```powershell
PS C:\test> Copy-Item -Path .\essai1.txt -Destination .\testdossier\

PS C:\test> Get-ChildItem -Path .\testdossier


    Repertoire : C:\test\testdossier


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        29/03/2025     18:02             15 essai1.txt
```

### 11) Afficher la liste des fichiers du dossier et des sous-dossiers de testPowerShell

> Pour ma part, des sous-dossiers de test

Commande :

```powershell
Get-ChildItem -Path .\..\test -Recurse -File
```

Retour :

```powershell
PS C:\test> Get-ChildItem -Path .\..\test -Recurse -File


    Repertoire : C:\test


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        29/03/2025     18:02             15 essai1.txt
-a----        29/03/2025     18:02             15 test2.txt


    Repertoire : C:\test\testdossier


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        29/03/2025     18:02             15 essai1.txt
```

### 12) Copier le dossier testdossier ( avec ses fichier ) dans un nouveau dossier test2dossier

Commande :

```powershell
Copy-Item -Path .\testdossier -Destination .\test2dossier -Recurse
```

Retour :

```powershell
PS C:\test> Copy-Item -Path .\testdossier -Destination .\test2dossier -Recurse

PS C:\test> Get-ChildItem


    Repertoire : C:\test


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        29/03/2025     18:10                test2dossier
d-----        29/03/2025     18:06                testdossier
-a----        29/03/2025     18:02             15 essai1.txt
-a----        29/03/2025     18:02             15 test2.txt

```

### 13) Deplacer le fichier test2.txt dans le dossier testdossier

Commande :

```powershell
Move-Item -Path .\test2.txt -Destination .\testdossier
```

Retour :

```powershell
PS C:\test> Move-Item -Path .\test2.txt -Destination .\testdossier

PS C:\test> Get-ChildItem -Path .\testdossier


    Repertoire : C:\test\testdossier


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        29/03/2025     18:02             15 essai1.txt
-a----        29/03/2025     18:02             15 test2.txt
```

### 14) Supprimer le dossier test2dossier (avec ses fichiers)

Commande :

```powershell
Remove-Item -Path .\test2dossier -Recurse -Force
```

Retour :

```powershell
PS C:\test> Remove-Item -Path .\test2dossier -Recurse

PS C:\test> Get-ChildItem


    Repertoire : C:\test


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        29/03/2025     18:12                testdossier
-a----        29/03/2025     18:02             15 essai1.txt
```

### 15) Tester l’existance du dossier c\... \ un_exemple, si le dossier existe affiche le texte en vert sinon en rouge

Commande :

```powershell
if (Test-Path "C:\test\un_exemple") {Write-Host "Le dossier existe." -ForegroundColor Green} else {Write-Host "Le dossier n existe pas." -ForegroundColor Red}
```

Retour :

```powershell
Le dossier n existe pas. # en rouge
```

### 15) Afficher la liste des .exe du dossier Windows

Commande :

```powershell
Get-ChildItem -Path C:\Windows -Filter *.exe
```

Retour :

```powershell
PS C:\test> Get-ChildItem -Path C:\Windows -Filter *.exe


    Repertoire : C:\Windows


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        19/02/2025     20:30          93696 bfsvc.exe
-a----        16/03/2025     15:07        5973416 explorer.exe
-a----        28/12/2024     16:35        1065984 HelpPane.exe
-a----        07/12/2019     10:09          18432 hh.exe
-a----        16/03/2025     15:07         200704 notepad.exe
-a----        28/12/2024     16:35         370176 regedit.exe
-a----        28/12/2024     16:34         164352 splwow64.exe
-a----        07/12/2019     10:10          11776 winhlp32.exe
-a----        06/12/2019     22:29          11264 write.exe
```

### 16) Puis afficher le nombre de fichier

Commande :

```powershell
(Get-ChildItem -Path C:\Windows -Filter *.exe).Count
```

Retour :

```powershell
PS C:\test> (Get-ChildItem -Path C:\Windows -Filter *.exe).Count
9
```

## Exercice 3 : Acces aux proprietes et aux methodes d'un objet

### 1) Affecter a la variable $loc , le resultat de la commande Get-Location

Commande :

```powershell
$loc = Get-Location
```

Retour :

```powershell
PS C:\test> $loc = Get-Location

PS C:\test>
```

### 2) Afficher les proprietes et les methodes de les methodes de la variable $loc

Commande :

```powershell
$loc | Get-Member
```

Retour :

```powershell
PS C:\test> $loc | Get-Member


   TypeName : System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

### 3) Afficher le chemin du dossier courant contenu dans cette variable

Commande :

```powershell
$loc.Path
```

Retour :

```powershell
PS C:\test> $loc.Path
C:\test
```

### 4) Afficher les informations sur le disque contenu par cette variable

Commande :

```powershell
$loc.Drive
```

Retour :

```powershell
Name           Used (GB)     Free (GB) Provider      Root   CurrentLocation
----           ---------     --------- --------      ----   ---------------
C                 302,01        628,91 FileSystem    C:\              'test
```

### 5) Affecter a la variable $lect, le resultat de la commande Get-PSDrive -Name C

Commande :

```powershell
$lect = Get-PSDrive -Name C
```

Retour :

```powershell
PS C:\test> $lect = Get-PSDrive -Name C

PS C:\test>
```

### 6) Afficher les proprietes et les methodes des methodes de la variable $lect

Commande :

```powershell
$lect | Get-Member
```

Retour :

```powershell
   TypeName : System.Management.Automation.PSDriveInfo

Name            MemberType     Definition
----            ----------     ----------
CompareTo       Method         int CompareTo(System.Management.Automation.PSDriveInfo drive), int CompareTo(System.Object obj), int IComparable.CompareTo(S...
Equals          Method         bool Equals(System.Object obj), bool Equals(System.Management.Automation.PSDriveInfo drive)
GetHashCode     Method         int GetHashCode()
GetType         Method         type GetType()
ToString        Method         string ToString()
Credential      Property       pscredential Credential {get;}
CurrentLocation Property       string CurrentLocation {get;set;}
Description     Property       string Description {get;set;}
DisplayRoot     Property       string DisplayRoot {get;}
MaximumSize     Property       System.Nullable[long] MaximumSize {get;}
Name            Property       string Name {get;}
Provider        Property       System.Management.Automation.ProviderInfo Provider {get;}
Root            Property       string Root {get;}
Free            ScriptProperty System.Object Free {get=## Ensure that this is a FileSystem drive...
Used            ScriptProperty System.Object Used {get=## Ensure that this is a FileSystem drive...
```

### 7) A partir de la variable $lect, afficher la description du lecteur C, afficher la taille en octet du volume utilise, afficher la taille en octet du volume libre.

Commande :

```powershell
PS C:\test> $lect.Description

PS C:\test> $lect.Used
324279726080

PS C:\test> $lect.Free
675280842752
```

### 8) Affecter a la variable $fichier , le resultat de la commande Get-childItem ..\essai1.txt

Commande :

```powershell
$fichier = Get-ChildItem ..\essai1.txt
```

Retour :

```powershell
PS C:\test\testdossier> $fichier = Get-ChildItem ..\essai1.txt

PS C:\test\testdossier>
```

### 9) Afficher les proprietes et les methodes de la variable $fichier

Commande :

```powershell
$fichier | Get-Member
```

Retour :

```powershell
   TypeName : System.IO.FileInfo

Name                      MemberType     Definition
----                      ----------     ----------
LinkType                  CodeProperty   System.String LinkType{get=GetLinkType;}
Mode                      CodeProperty   System.String Mode{get=Mode;}
Target                    CodeProperty   System.Collections.Generic.IEnumerable`1[[System.String, mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToke...]]
AppendText                Method         System.IO.StreamWriter AppendText()
CopyTo                    Method         System.IO.FileInfo CopyTo(string destFileName), System.IO.FileInfo CopyTo(string destFileName, bool overwrite)
Create                    Method         System.IO.FileStream Create()
CreateObjRef              Method         System.Runtime.Remoting.ObjRef CreateObjRef(type requestedType)
CreateText                Method         System.IO.StreamWriter CreateText()
Decrypt                   Method         void Decrypt()
Delete                    Method         void Delete()
Encrypt                   Method         void Encrypt()
Equals                    Method         bool Equals(System.Object obj)
GetAccessControl          Method         System.Security.AccessControl.FileSecurity GetAccessControl(), System.Security.AccessControl.FileSecurity GetAcces...
GetHashCode               Method         int GetHashCode()
GetLifetimeService        Method         System.Object GetLifetimeService()
GetObjectData             Method         void GetObjectData(System.Runtime.Serialization.SerializationInfo info, System.Runtime.Serialization.StreamingCont...
GetType                   Method         type GetType()
InitializeLifetimeService Method         System.Object InitializeLifetimeService()
MoveTo                    Method         void MoveTo(string destFileName)
Open                      Method         System.IO.FileStream Open(System.IO.FileMode mode), System.IO.FileStream Open(System.IO.FileMode mode, System.IO.F...
OpenRead                  Method         System.IO.FileStream OpenRead()
OpenText                  Method         System.IO.StreamReader OpenText()
OpenWrite                 Method         System.IO.FileStream OpenWrite()
Refresh                   Method         void Refresh()
Replace                   Method         System.IO.FileInfo Replace(string destinationFileName, string destinationBackupFileName), System.IO.FileInfo Repla...
SetAccessControl          Method         void SetAccessControl(System.Security.AccessControl.FileSecurity fileSecurity)
ToString                  Method         string ToString()
PSChildName               NoteProperty   string PSChildName=essai1.txt
PSDrive                   NoteProperty   PSDriveInfo PSDrive=C
PSIsContainer             NoteProperty   bool PSIsContainer=False
PSParentPath              NoteProperty   string PSParentPath=Microsoft.PowerShell.Core\FileSystem::C:\test
PSPath                    NoteProperty   string PSPath=Microsoft.PowerShell.Core\FileSystem::C:\test\essai1.txt
PSProvider                NoteProperty   ProviderInfo PSProvider=Microsoft.PowerShell.Core\FileSystem
Attributes                Property       System.IO.FileAttributes Attributes {get;set;}
CreationTime              Property       datetime CreationTime {get;set;}
CreationTimeUtc           Property       datetime CreationTimeUtc {get;set;}
Directory                 Property       System.IO.DirectoryInfo Directory {get;}
DirectoryName             Property       string DirectoryName {get;}
Exists                    Property       bool Exists {get;}
Extension                 Property       string Extension {get;}
FullName                  Property       string FullName {get;}
IsReadOnly                Property       bool IsReadOnly {get;set;}
LastAccessTime            Property       datetime LastAccessTime {get;set;}
LastAccessTimeUtc         Property       datetime LastAccessTimeUtc {get;set;}
LastWriteTime             Property       datetime LastWriteTime {get;set;}
LastWriteTimeUtc          Property       datetime LastWriteTimeUtc {get;set;}
Length                    Property       long Length {get;}
Name                      Property       string Name {get;}
BaseName                  ScriptProperty System.Object BaseName {get=if ($this.Extension.Length -gt 0){$this.Name.Remove($this.Name.Length - $this.Extensio...
VersionInfo               ScriptProperty System.Object VersionInfo {get=[System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName);}
```

### 10) A partir de la variable $fichier, afficher le nom du fichier et la date du dernier acces

Commande :

```powershell
$fichier.Name
$fichier.LastAccessTime
```

Retour :

```powershell
PS C:\test\testdossier> $fichier.Name
essai1.txt

PS C:\test\testdossier> $fichier.LastAccessTime

samedi 29 mars 2025 18:02:56
```

### 11) A l'aide d'une methode de la variable $fichier, copier ce fichier dans un nouveau fichier nomme C:\TestPowerShell\essai2.txt

Commande :

```powershell
$fichier.CopyTo("C:\test\essai2.txt")
```

Retour :

```powershell
PS C:\test\testdossier> $fichier.CopyTo("C:\test\essai2.txt")

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        29/03/2025     18:02             15 essai2.txt
```

<div style="color: red;">

> J'ai decide de ne pas creer un dossier TestPowerShell car je possede deja un dossier test dedie. Donc dans la commande j'ai remplace C:\TestPowerShell\essai2.txt par C:\test\essai2.txt

</div>

### 12) A partir de la variable $fichier, supprimer le fichier essai1.txt

Commande :

```powershell
$fichier.Delete()
```

Retour :

```powershell
PS C:\test\testdossier> $fichier.Delete()

PS C:\test\testdossier> Get-ChildItem


    Repertoire : C:\test\testdossier


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        29/03/2025     18:02             15 essai1.txt
-a----        29/03/2025     18:02             15 test2.txt
```

### 13) Lancer notepad.exe et reduire la fenetre du block notes

Commande :

```powershell
Start-Process notepad.exe -WindowStyle Minimized
```

### 14) Lancer la comande Get-Process et verifier que le bloc-notes soit bien dans les processus actif

Commande :

```powershell
PS C:\test\testdossier> Get-Process notepad

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    194      12     2320      12440       0,03   7660   1 notepad
```

### 15) Affecter a la variable $proc, le resultat de la commande Get-Process notepad

Commande :

```powershell
PS C:\test\testdossier> $proc = Get-Process notepad

PS C:\test\testdossier>
```

### 16) Afficher les proprietes et les methodes de la variable $proc

Commande :

```powershell
PS C:\test\testdossier> $proc | Get-Member


   TypeName : System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
NPM                        AliasProperty  NPM = NonpagedSystemMemorySize64
PM                         AliasProperty  PM = PagedMemorySize64
SI                         AliasProperty  SI = SessionId
VM                         AliasProperty  VM = VirtualMemorySize64
WS                         AliasProperty  WS = WorkingSet64
Disposed                   Event          System.EventHandler Disposed(System.Object, System.EventArgs)
ErrorDataReceived          Event          System.Diagnostics.DataReceivedEventHandler ErrorDataReceived(System.Object, System.Diagnostics.DataReceivedEvent...
Exited                     Event          System.EventHandler Exited(System.Object, System.EventArgs)
OutputDataReceived         Event          System.Diagnostics.DataReceivedEventHandler OutputDataReceived(System.Object, System.Diagnostics.DataReceivedEven...
BeginErrorReadLine         Method         void BeginErrorReadLine()
BeginOutputReadLine        Method         void BeginOutputReadLine()
CancelErrorRead            Method         void CancelErrorRead()
CancelOutputRead           Method         void CancelOutputRead()
Close                      Method         void Close()
CloseMainWindow            Method         bool CloseMainWindow()
CreateObjRef               Method         System.Runtime.Remoting.ObjRef CreateObjRef(type requestedType)
Dispose                    Method         void Dispose(), void IDisposable.Dispose()
Equals                     Method         bool Equals(System.Object obj)
GetHashCode                Method         int GetHashCode()
GetLifetimeService         Method         System.Object GetLifetimeService()
GetType                    Method         type GetType()
InitializeLifetimeService  Method         System.Object InitializeLifetimeService()
Kill                       Method         void Kill()
Refresh                    Method         void Refresh()
Start                      Method         bool Start()
ToString                   Method         string ToString()
WaitForExit                Method         bool WaitForExit(int milliseconds), void WaitForExit()
WaitForInputIdle           Method         bool WaitForInputIdle(int milliseconds), bool WaitForInputIdle()
__NounName                 NoteProperty   string __NounName=Process
BasePriority               Property       int BasePriority {get;}
Container                  Property       System.ComponentModel.IContainer Container {get;}
EnableRaisingEvents        Property       bool EnableRaisingEvents {get;set;}
ExitCode                   Property       int ExitCode {get;}
ExitTime                   Property       datetime ExitTime {get;}
Handle                     Property       System.IntPtr Handle {get;}
HandleCount                Property       int HandleCount {get;}
HasExited                  Property       bool HasExited {get;}
Id                         Property       int Id {get;}
MachineName                Property       string MachineName {get;}
MainModule                 Property       System.Diagnostics.ProcessModule MainModule {get;}
MainWindowHandle           Property       System.IntPtr MainWindowHandle {get;}
MainWindowTitle            Property       string MainWindowTitle {get;}
MaxWorkingSet              Property       System.IntPtr MaxWorkingSet {get;set;}
MinWorkingSet              Property       System.IntPtr MinWorkingSet {get;set;}
Modules                    Property       System.Diagnostics.ProcessModuleCollection Modules {get;}
NonpagedSystemMemorySize   Property       int NonpagedSystemMemorySize {get;}
NonpagedSystemMemorySize64 Property       long NonpagedSystemMemorySize64 {get;}
PagedMemorySize            Property       int PagedMemorySize {get;}
PagedMemorySize64          Property       long PagedMemorySize64 {get;}
PagedSystemMemorySize      Property       int PagedSystemMemorySize {get;}
PagedSystemMemorySize64    Property       long PagedSystemMemorySize64 {get;}
PeakPagedMemorySize        Property       int PeakPagedMemorySize {get;}
PeakPagedMemorySize64      Property       long PeakPagedMemorySize64 {get;}
PeakVirtualMemorySize      Property       int PeakVirtualMemorySize {get;}
PeakVirtualMemorySize64    Property       long PeakVirtualMemorySize64 {get;}
PeakWorkingSet             Property       int PeakWorkingSet {get;}
PeakWorkingSet64           Property       long PeakWorkingSet64 {get;}
PriorityBoostEnabled       Property       bool PriorityBoostEnabled {get;set;}
PriorityClass              Property       System.Diagnostics.ProcessPriorityClass PriorityClass {get;set;}
PrivateMemorySize          Property       int PrivateMemorySize {get;}
PrivateMemorySize64        Property       long PrivateMemorySize64 {get;}
PrivilegedProcessorTime    Property       timespan PrivilegedProcessorTime {get;}
ProcessName                Property       string ProcessName {get;}
ProcessorAffinity          Property       System.IntPtr ProcessorAffinity {get;set;}
Responding                 Property       bool Responding {get;}
SafeHandle                 Property       Microsoft.Win32.SafeHandles.SafeProcessHandle SafeHandle {get;}
SessionId                  Property       int SessionId {get;}
Site                       Property       System.ComponentModel.ISite Site {get;set;}
StandardError              Property       System.IO.StreamReader StandardError {get;}
StandardInput              Property       System.IO.StreamWriter StandardInput {get;}
StandardOutput             Property       System.IO.StreamReader StandardOutput {get;}
StartInfo                  Property       System.Diagnostics.ProcessStartInfo StartInfo {get;set;}
StartTime                  Property       datetime StartTime {get;}
SynchronizingObject        Property       System.ComponentModel.ISynchronizeInvoke SynchronizingObject {get;set;}
Threads                    Property       System.Diagnostics.ProcessThreadCollection Threads {get;}
TotalProcessorTime         Property       timespan TotalProcessorTime {get;}
UserProcessorTime          Property       timespan UserProcessorTime {get;}
VirtualMemorySize          Property       int VirtualMemorySize {get;}
VirtualMemorySize64        Property       long VirtualMemorySize64 {get;}
WorkingSet                 Property       int WorkingSet {get;}
WorkingSet64               Property       long WorkingSet64 {get;}
PSConfiguration            PropertySet    PSConfiguration {Name, Id, PriorityClass, FileVersion}
PSResources                PropertySet    PSResources {Name, Id, Handlecount, WorkingSet, NonPagedMemorySize, PagedMemorySize, PrivateMemorySize, VirtualMe...
Company                    ScriptProperty System.Object Company {get=$this.Mainmodule.FileVersionInfo.CompanyName;}
CPU                        ScriptProperty System.Object CPU {get=$this.TotalProcessorTime.TotalSeconds;}
Description                ScriptProperty System.Object Description {get=$this.Mainmodule.FileVersionInfo.FileDescription;}
FileVersion                ScriptProperty System.Object FileVersion {get=$this.Mainmodule.FileVersionInfo.FileVersion;}
Path                       ScriptProperty System.Object Path {get=$this.Mainmodule.FileName;}
Product                    ScriptProperty System.Object Product {get=$this.Mainmodule.FileVersionInfo.ProductName;}
ProductVersion             ScriptProperty System.Object ProductVersion {get=$this.Mainmodule.FileVersionInfo.ProductVersion;}
```

### 17) A partir de la variable $proc, afficher la description du processus

Commande :

```powershell
$proc.Description
```

Retour :

```powershell
PS C:\test\testdossier> $proc.Description
Bloc-notes

PS C:\test\testdossier>
```

### 18) Afficher le chemin d'acces de l'executable

Commande :

```powershell
$proc.Path
```

Retour :

```powershell
PS C:\test\testdossier> $proc.Path
C:\Windows\system32\notepad.exe

PS C:\test\testdossier>
```

## Exercice 4 : Monitoring

```powershell
# Dans un fichier monitoring.ps1
# Afficher le nom de la session et la date/heure
Write-Host "Nom de la session : $env:USERNAME" -ForegroundColor Cyan
Write-Host "Date et heure du jour : $(Get-Date)" -ForegroundColor Cyan
Write-Host "---------------------------------------------" -ForegroundColor Cyan

# Recuperer et afficher la version de Windows
$os = Get-CimInstance Win32_OperatingSystem
Write-Host "Systeme d'exploitation : $($os.Caption) - Version $($os.Version)" -ForegroundColor Green
Write-Host "---------------------------------------------" -ForegroundColor Green

# Liste des disques avec leur espace libre et alerte si espace critique
Write-Host "Liste des disques : " -ForegroundColor Yellow
$drives = Get-PSDrive -PSProvider FileSystem

foreach ($drive in $drives) {
    $totalSize = $drive.Used + $drive.Free  # Capacite totale du disque
    $freePercent = [math]::Round(($drive.Free / $totalSize) * 100, 2)  # Pourcentage d'espace libre

    # Verification du type de disque (SSD ou HDD)
    $disk = Get-PhysicalDisk | Where-Object { $_.DeviceID -eq $drive.Root[0] }
    $isSSD = $disk.MediaType -eq "SSD"

    # Definition du seuil critique (10% pour HDD, 20% pour SSD)
    $threshold = if ($isSSD) { 20 } else { 10 }

    # Affichage du disque
    if ($freePercent -lt $threshold) {
        Write-Host "ALERTE: Le disque $($drive.Name) n'a que $freePercent% d'espace libre !" -ForegroundColor Red
    } else {
        Write-Host "Disque $($drive.Name) - Espace libre : $($drive.Free / 1GB) Go ($freePercent%)" -ForegroundColor White
    }
}
Write-Host "---------------------------------------------" -ForegroundColor Yellow

# Liste des partages reseau
Write-Host "Liste des partages reseau :" -ForegroundColor Magenta
Get-SmbShare | Select-Object Name, Path, Description | Format-Table -AutoSize
```

---

### <u>Explication du script :</u>

- Affiche le nom de la session et la date/heure actuelle.

- Recupere la version de Windows.

- Liste les disques disponibles avec leur espace libre restant.

  - Si un disque a moins de 10% d'espace libre (HDD) ou moins de 20% (SSD), une alerte rouge s'affiche.

- Verifie si le disque est SSD ou HDD et applique les seuils critiques en consequence.

- Affiche la liste des partages reseau.

---

### <u>Comment executer le script ?</u>

- Ouvrir PowerShell en tant qu'administrateur.

- Aller dans le dossier où se trouve le script :

```powershell
cd "C:\chemin\du\script"
```

- Lancer le script :

```powershell
.\monitoring.ps1
```

### <u>Bonus</u>

```powershell
# Definir le fichier HTML de sortie dans le dossier www de laragon
$outputHtml = "C:\Users\yulia\Downloads\laragon-6.0.0\www\index.html"

# Creation de l'objet HTML
$html = @"
<html>
<head>
    <title>Rapport Systeme</title>
    <style>
        body { font-family: Arial, sans-serif; }
        h1 { color: #0078D7; }
        table { width: 100%; border-collapse: collapse; }
        th, td { border: 1px solid black; padding: 8px; text-align: left; }
        th { background-color: #0078D7; color: white; }
        .alert { color: red; font-weight: bold; }
    </style>
</head>
<body>
<h1>Rapport Systeme</h1>
<p><strong>Nom de la session :</strong> $env:USERNAME</p>
<p><strong>Date et heure :</strong> $(Get-Date)</p>
<hr>
<h2>Systeme d'exploitation</h2>
<p><strong>Version :</strong> $(Get-CimInstance Win32_OperatingSystem).Caption</p>
<p><strong>Numero de version :</strong> $(Get-CimInstance Win32_OperatingSystem).Version</p>
<hr>
<h2>Disques et espace libre</h2>
<table>
<tr><th>Nom</th><th>Espace Libre (Go)</th><th>Pourcentage Libre</th></tr>
"@

# Recuperation des disques et gestion des alertes
$drives = Get-PSDrive -PSProvider FileSystem
foreach ($drive in $drives) {
    $totalSize = $drive.Used + $drive.Free
    $freePercent = [math]::Round(($drive.Free / $totalSize) * 100, 2)

    # Verification SSD ou HDD
    $disk = Get-PhysicalDisk | Where-Object { $_.DeviceID -eq $drive.Root[0] }
    $isSSD = $disk.MediaType -eq "SSD"
    $threshold = if ($isSSD) { 20 } else { 10 }

    # Detection d'alerte rouge si espace faible
    $alertClass = if ($freePercent -lt $threshold) { "alert" } else { "" }

    $html += "<tr><td>$($drive.Name)</td><td>$([math]::Round($drive.Free / 1GB, 2))</td><td class='$alertClass'>$freePercent%</td></tr>"
}

$html += "</table><hr>"

# Liste des partages reseau
$html += "<h2>Partages Reseau</h2><table><tr><th>Nom</th><th>Chemin</th></tr>"
$shares = Get-SmbShare | Select-Object Name, Path
foreach ($share in $shares) {
    $html += "<tr><td>$($share.Name)</td><td>$($share.Path)</td></tr>"
}
$html += "</table></body></html>"

# Sauvegarde du fichier HTML
$html | Out-File -Encoding utf8 $outputHtml

Write-Host "Rapport genere !" -ForegroundColor Green
```

---

### Commandes Utilisees

#### **1. Recuperation des Informations Systeme**

##### **Nom de la session et Date/Heure**

```powershell
$env:USERNAME
Get-Date
```

- `$env:USERNAME` → Recupere le **nom de l'utilisateur connecte**
- `Get-Date` → Affiche la **date et l'heure actuelles**

---

#### **2. Recuperation de la Version du Systeme d'Exploitation**

```powershell
Get-CimInstance Win32_OperatingSystem
```

- `Get-CimInstance` permet d'interroger **WMI (Windows Management Instrumentation)**
- `Win32_OperatingSystem` contient des infos comme **le nom de Windows, la version, l'architecture**

---

#### **3. Liste des Disques avec Espace Libre**

```powershell
$drives = Get-PSDrive -PSProvider FileSystem
```

- `Get-PSDrive` → Liste tous les lecteurs logiques
- `-PSProvider FileSystem` → Filtre pour ne garder que les lecteurs **de type disque**

##### **Calcul de l'espace total et du pourcentage libre**

```powershell
$totalSize = $drive.Used + $drive.Free
$freePercent = [math]::Round(($drive.Free / $totalSize) * 100, 2)
```

- `drive.Used` → Recupere l'espace **utilise** en octets
- `drive.Free` → Recupere l'espace **disponible** en octets
- `math::Round()` → Arrondit le pourcentage d'espace libre

---

#### **4. Verification du Type de Disque (SSD ou HDD)**

```powershell
$disk = Get-PhysicalDisk | Where-Object { $_.DeviceID -eq $drive.Root[0] }
$isSSD = $disk.MediaType -eq "SSD"
```

- `Get-PhysicalDisk` → Liste les **disques physiques (SSD, HDD, USB, etc.)**
- `Where-Object` → Filtre pour obtenir **le disque correspondant au lecteur**
- `$isSSD` → Stocke `True` si le disque est un SSD

##### **Definition des seuils d'alerte**

```powershell
$threshold = if ($isSSD) { 20 } else { 10 }
```

- Seuil de **10%** pour les **HDD**
- Seuil de **20%** pour les **SSD**

##### **Affichage des Alertes en Rouge**

```powershell
$alertClass = if ($freePercent -lt $threshold) { "alert" } else { "" }
```

- Si l'espace libre est **inferieur au seuil**, une **alerte est activee**

---

#### **5. Liste des Partages Reseau**

```powershell
Get-SmbShare | Select-Object Name, Path
```

- `Get-SmbShare` → Liste les **partages reseau** sur le PC
- `Select-Object Name, Path` → Garde **uniquement le nom du partage et son chemin**

---

#### **6. Generation du Fichier HTML**

```powershell
$outputHtml = "C:\Temp\SystemInfo.html"
$html | Out-File -Encoding utf8 $outputHtml
```

- `$outputHtml` → Definit l'**emplacement du fichier HTML**
- `Out-File -Encoding utf8` → **Sauvegarde les donnees en UTF-8**

#### **Bonus pour le serveur web**

```powershell
$outputHtml = "C:\Users\yulia\Downloads\laragon-6.0.0\www\index.html"
```

> Pour l'afficher dans un serveur Web. Il m'a suffit de lancer le serveur web de laragon. Puis de me rendre sur la page web.
>
> Cela fonctionne car le fichier `index.html` se trouve dans le dossier racine de laragon.

---

## Exercice 5 : Les services

```powershell
# Dans un fichier services.ps1
# Demande a l'utilisateur d'entrer un nom de service ou un mot-cle
$search = Read-Host "Entrez un mot-cle pour rechercher un service"

# Recupere les services correspondant a la recherche
$services = Get-Service | Where-Object { $_.Name -like "*$search*" -or $_.DisplayName -like "*$search*" }

# Verifie s'il y a des resultats
if ($services.Count -eq 0) {
    Write-Host "Aucun service trouve pour '$search'." -ForegroundColor Red
    exit
}

# Affichage de la liste des services trouves avec leur etat
Write-Host "`nListe des services trouves :"
$index = 1
foreach ($service in $services) {
    $color = if ($service.Status -eq "Running") { "Green" } else { "Red" }
    Write-Host "$index. $($service.DisplayName) ($($service.Name)) - [$($service.Status)]" -ForegroundColor $color
    $index++
}

# Demande a l'utilisateur de choisir un service par son numero
$choice = Read-Host "Entrez le numero du service a gerer"

# Verifie que l'entree est un nombre valide
if ($choice -notmatch '^\d+$' -or [int]$choice -lt 1 -or [int]$choice -gt $services.Count) {
    Write-Host "Numero invalide." -ForegroundColor Red
    exit
}

# Selectionne le service choisi
$selectedService = $services[[int]$choice - 1]
Write-Host "`nService selectionne : $($selectedService.DisplayName) ($($selectedService.Name)) - [$($selectedService.Status)]"

# Propose une action en fonction de l'etat du service
if ($selectedService.Status -eq "Running") {
    $confirm = Read-Host "Le service est en cours d'execution. Voulez-vous l'arreter ? (O/N)"
    if ($confirm -match "^[Oo]$") {
        Stop-Service -Name $selectedService.Name -Force
        Write-Host "Service arrete : $($selectedService.DisplayName)" -ForegroundColor Yellow
    } else {
        Write-Host "Aucune action effectuee."
    }
} else {
    $confirm = Read-Host "Le service est arrete. Voulez-vous le demarrer ? (O/N)"
    if ($confirm -match "^[Oo]$") {
        Start-Service -Name $selectedService.Name
        Write-Host "Service demarre : $($selectedService.DisplayName)" -ForegroundColor Green
    } else {
        Write-Host "Aucune action effectuee."
    }
}

# Affichage final du nouvel etat du service
$updatedService = Get-Service -Name $selectedService.Name
Write-Host "Nouvel etat du service : $($updatedService.Status)" -ForegroundColor Cyan
```

### Explication du script

- Recherche des services contenant un mot-cle fourni par l'utilisateur.

- Affichage des services trouves avec :

  - Vert si le service est demarre

  - Rouge si le service est arrete

- Selection d'un service par numero.

- Demande de confirmation avant d'effectuer une action :

  - Si le service est demarre, l'utilisateur peut l'arreter.

  - Si le service est arrete, l'utilisateur peut le demarrer.

- Affichage du nouvel etat du service apres modification.

### Exemple d'utilisation :

#### Execution du script :

- Ouvrir PowerShell en tant qu'administrateur
- Executer le script :

```powershell
.\services.ps1
```

#### Exemple :

```powershell
Entrez un mot-cle pour rechercher un service: spooler

Liste des services trouves :
1. Spouleur d impression (Spooler) - [Running]

Entrez le numero du service a gerer: 1

Service selectionne : Spouleur d impression (Spooler) - [Running]
Le service est en cours d execution. Voulez-vous l arreter ? (O/N): O
Service arrete : Spouleur d impression
Nouvel etat du service : Stopped
```

---

### **Commandes Utilisees**

#### **1. Recherche des Services Windows**

```powershell
$search = Read-Host "Entrez un mot-cle pour rechercher un service"
```

- `Read-Host` → Demande a l'utilisateur de saisir un texte (mot-cle pour rechercher un service).
- Stocke l'entree dans la variable `$search`.

```powershell
$services = Get-Service | Where-Object { $_.Name -like "*$search*" -or $_.DisplayName -like "*$search*" }
```

- `Get-Service` → Liste **tous les services Windows**.
- `Where-Object` → Filtre la liste pour afficher uniquement les services **dont le nom ou l'affichage contient** le mot-cle entre.
  - `-like "*$search*"` → Recherche **partielle** (exemple : "print" trouve "Spooler").

---

#### **2. Verification du Resultat**

```powershell
if ($services.Count -eq 0) {
    Write-Host "Aucun service trouve pour '$search'." -ForegroundColor Red
    exit
}
```

- `if ($services.Count -eq 0)` → Verifie si aucun service ne correspond a la recherche.
- `Write-Host "..."` → Affiche un **message rouge** si aucun service trouve.
- `exit` → **Arrete le script** immediatement.

---

#### **3. Affichage des Services Trouves avec Leur etat**

```powershell
$index = 1
foreach ($service in $services) {
    $color = if ($service.Status -eq "Running") { "Green" } else { "Red" }
    Write-Host "$index. $($service.DisplayName) ($($service.Name)) - [$($service.Status)]" -ForegroundColor $color
    $index++
}
```

- **Boucle `foreach`** → Parcourt chaque service trouve.
- `$service.Status` → Recupere l'etat du service (`Running` ou `Stopped`).
- **Definition d'une couleur** :
  - `"Green"` si le service est **demarre**.
  - `"Red"` si le service est **arrete**.
- `Write-Host` → Affiche la liste des services avec **un numero**, leur **nom affiche**, leur **nom technique** et leur **etat** en couleur.
- `$index++` → Incremente le numero affiche.

---

#### **4. Selection d'un Service par l'Utilisateur**

```powershell
$choice = Read-Host "Entrez le numero du service a gerer"
```

- `Read-Host` → Demande a l'utilisateur de choisir un **numero de service**.

```powershell
if ($choice -notmatch '^\d+$' -or [int]$choice -lt 1 -or [int]$choice -gt $services.Count) {
    Write-Host "Numero invalide." -ForegroundColor Red
    exit
}
```

- **Validation de l'entree utilisateur** :
  - `-notmatch '^\d+$'` → Verifie que l'entree est **un nombre entier**.
  - `[int]$choice -lt 1` → Verifie que le numero est **au moins 1**.
  - `[int]$choice -gt $services.Count` → Verifie que le numero **existe** dans la liste.
- **Si la saisie est invalide**, affiche un **message d'erreur rouge** et **quitte le script**.

---

#### **5. Recuperation du Service Selectionne**

```powershell
$selectedService = $services[[int]$choice - 1]
Write-Host "`nService selectionne : $($selectedService.DisplayName) ($($selectedService.Name)) - [$($selectedService.Status)]"
```

- **Selectionne le service choisi** en convertissant l'entree en **indice de tableau** (`-1` car les index commencent a 0).
- `Write-Host` → Affiche le **nom du service selectionne** et son **etat actuel**.

---

#### **6. Arret ou Demarrage du Service**

##### **Si le service est en cours d'execution (`Running`)**

```powershell
if ($selectedService.Status -eq "Running") {
    $confirm = Read-Host "Le service est en cours d'execution. Voulez-vous l'arreter ? (O/N)"
    if ($confirm -match "^[Oo]$") {
        Stop-Service -Name $selectedService.Name -Force
        Write-Host "Service arrete : $($selectedService.DisplayName)" -ForegroundColor Yellow
    } else {
        Write-Host "Aucune action effectuee."
    }
}
```

- **Verifie si le service est en cours d'execution (`Running`)**.
- `Read-Host` demande **confirmation** a l'utilisateur.
- `if ($confirm -match "^[Oo]$")` → Verifie si l'utilisateur a entre `O` ou `o` pour **confirmer**.
- `Stop-Service -Name $selectedService.Name -Force`
  - **Arrete** le service selectionne.
  - `-Force` → **Forcer l'arret** si necessaire.
- `Write-Host` affiche un message **jaune** si le service a ete arrete.

---

##### **Si le service est arrete (`Stopped`)**

```powershell
else {
    $confirm = Read-Host "Le service est arrete. Voulez-vous le demarrer ? (O/N)"
    if ($confirm -match "^[Oo]$") {
        Start-Service -Name $selectedService.Name
        Write-Host "Service demarre : $($selectedService.DisplayName)" -ForegroundColor Green
    } else {
        Write-Host "Aucune action effectuee."
    }
}
```

- **Si le service est arrete (`Stopped`)**, propose a l'utilisateur de **le demarrer**.
- `Start-Service -Name $selectedService.Name` → **Demarre** le service.
- `Write-Host` affiche un message **vert** si le service a ete demarre.

---

#### **7. Verification de l'etat Final du Service**

```powershell
$updatedService = Get-Service -Name $selectedService.Name
Write-Host "Nouvel etat du service : $($updatedService.Status)" -ForegroundColor Cyan
```

- **Reprend l'etat du service** apres l'action.
- `Write-Host` affiche son **etat actuel en cyan**.

---

## Exercice 6 : Archive structuree

```powershell
# Dans un fichier structures.ps1
# Demande a l'utilisateur de saisir le chemin du dossier a organiser
$sourceFolder = Read-Host "Entrez le chemin du dossier a archiver"

# Verifie si le dossier existe
if (-not (Test-Path $sourceFolder)) {
    Write-Host "Le dossier specifie n'existe pas." -ForegroundColor Red
    exit
}

# Creation du dossier d'archivage
$archiveFolder = "$sourceFolder\Archive"
if (-not (Test-Path $archiveFolder)) {
    New-Item -ItemType Directory -Path $archiveFolder | Out-Null
}

# Definition des extensions pour chaque categorie
$categories = @{
    "Documents" = @("doc", "docx", "xls", "xlsx", "pdf", "txt")
    "Images" = @("jpg", "jpeg", "png", "gif", "bmp", "tiff")
    "Videos" = @("mp4", "avi", "mkv", "mov", "wmv")
}

# Creation des dossiers de tri
$folders = @{}
foreach ($category in $categories.Keys) {
    $folderPath = "$archiveFolder\$category"
    if (-not (Test-Path $folderPath)) {
        New-Item -ItemType Directory -Path $folderPath | Out-Null
    }
    $folders[$category] = $folderPath
}

# Dossier pour les fichiers non classes
$otherFolder = "$archiveFolder\Autres"
if (-not (Test-Path $otherFolder)) {
    New-Item -ItemType Directory -Path $otherFolder | Out-Null
}
$folders["Autres"] = $otherFolder

# Deplacement des fichiers
Get-ChildItem -Path $sourceFolder -File | ForEach-Object {
    $file = $_
    $ext = $file.Extension.TrimStart('.').ToLower()  # Recupere l'extension en minuscule
    $destination = $otherFolder  # Par defaut, les fichiers vont dans "Autres"

    foreach ($category in $categories.Keys) {
        if ($ext -in $categories[$category]) {
            $destination = $folders[$category]
            break
        }
    }

    Move-Item -Path $file.FullName -Destination $destination -Force
}

# Renommage des dossiers avec le nombre de fichiers
foreach ($category in $folders.Keys) {
    $folderPath = $folders[$category]
    $count = (Get-ChildItem -Path $folderPath -File).Count
    if ($count -gt 0) {
        Rename-Item -Path $folderPath -NewName "$folderPath ($count)" -Force
    }
}

# Creation de l'archive ZIP avec la date et l'heure
$date = Get-Date -Format "yyyy-MM-dd_HH-mm-ss"
$zipFile = "$sourceFolder\Archive_$date.zip"
Compress-Archive -Path "$archiveFolder\*" -DestinationPath $zipFile -Force

Write-Host "Archive creee : $zipFile" -ForegroundColor Green

# Verification de la presence d'une cle USB
$usbDrive = Get-PSDrive -PSProvider FileSystem | Where-Object { $_.Root -match "^[D-Z]:\\" }

if ($usbDrive) {
    $usbPath = "$($usbDrive.Root)\$([System.IO.Path]::GetFileName($zipFile))"
    Copy-Item -Path $zipFile -Destination $usbPath -Force
    Write-Host "Archive copiee sur la cle USB : $usbPath" -ForegroundColor Cyan
} else {
    Write-Host "Aucune cle USB detectee." -ForegroundColor Yellow
}
```

### Exemple d'Utilisation

#### 1. Execution du script

- Ouvrir PowerShell en tant qu'administrateur

- Executer le script :

```powershell
.\structures.ps1
```

#### 2. Exemple

L'utilisateur doit saisir le chemin du dossier a organiser :

```powershell
Entrez le chemin du dossier a archiver: C:\Users\MonPC\Documents\Test
```

#### 3. Resultat apres execution

- Creation d'un dossier "Archive" dans C:\Users\MonPC\Documents\Test

- Tri des fichiers dans :

  - Documents (3) → 3 fichiers Word, PDF, ...

  - Images (5) → 5 fichiers JPG, PNG, ...

  - Videos (2) → 2 fichiers MP4, ...

  - Autres (1) → 1 fichier inconnu

- Creation d'une archive ZIP nommee :

  ```makefile
  C:\Users\MonPC\Documents\Test\Archive_2025-03-28_14-30-15.zip
  ```

- Copie sur la cle USB F:\Archive_2025-03-28_14-30-15.zip

---

### Commandes Utilisees

#### **1. Saisie du chemin du dossier**

```powershell
$sourceFolder = Read-Host "Entrez le chemin du dossier a archiver"
```

- `Read-Host` → Demande a l'utilisateur de saisir **le dossier source**
- Stocke la saisie dans `$sourceFolder`

---

#### **2. Verification de l'existence du dossier**

```powershell
if (-not (Test-Path $sourceFolder)) {
    Write-Host "Le dossier specifie n'existe pas." -ForegroundColor Red
    exit
}
```

- `Test-Path $sourceFolder` → **Verifie si le dossier existe**
- Si le dossier **n'existe pas**, affiche une erreur et **quitte le script** (`exit`)

---

#### **3. Creation du dossier "Archive"**

```powershell
$archiveFolder = "$sourceFolder\Archive"
if (-not (Test-Path $archiveFolder)) {
    New-Item -ItemType Directory -Path $archiveFolder | Out-Null
}
```

- Definit `$archiveFolder` comme `C:\...\Archive`
- `New-Item -ItemType Directory` → **Cree le dossier "Archive"** s'il n'existe pas

---

#### **4. Definition des categories de fichiers**

```powershell
$categories = @{
    "Documents" = @("doc", "docx", "xls", "xlsx", "pdf", "txt")
    "Images" = @("jpg", "jpeg", "png", "gif", "bmp", "tiff")
    "Videos" = @("mp4", "avi", "mkv", "mov", "wmv")
}
```

- Cree une **table de hachage** (`@{}`) pour classer les extensions de fichiers (comme un dictionnaire en Python)

---

#### **5. Creation des dossiers pour chaque categorie**

```powershell
$folders = @{}
foreach ($category in $categories.Keys) {
    $folderPath = "$archiveFolder\$category"
    if (-not (Test-Path $folderPath)) {
        New-Item -ItemType Directory -Path $folderPath | Out-Null
    }
    $folders[$category] = $folderPath
}
```

- Parcourt **toutes les categories** (`Documents`, `Images`, `Videos`)
- **Cree un dossier** pour chaque categorie
- Stocke le **chemin du dossier** dans `$folders`

---

#### **6. Creation du dossier "Autres"**

```powershell
$otherFolder = "$archiveFolder\Autres"
if (-not (Test-Path $otherFolder)) {
    New-Item -ItemType Directory -Path $otherFolder | Out-Null
}
$folders["Autres"] = $otherFolder
```

- Cree un **dossier pour les fichiers non classes**
- Ajoute son chemin a `$folders`

---

#### **7. Tri et deplacement des fichiers**

```powershell
Get-ChildItem -Path $sourceFolder -File | ForEach-Object {
    $file = $_
    $ext = $file.Extension.TrimStart('.').ToLower()
    $destination = $otherFolder

    foreach ($category in $categories.Keys) {
        if ($ext -in $categories[$category]) {
            $destination = $folders[$category]
            break
        }
    }

    Move-Item -Path $file.FullName -Destination $destination -Force
}
```

- `Get-ChildItem -Path $sourceFolder -File` → Liste **tous les fichiers** du dossier
- Convertit **l'extension en minuscule**
- **Teste chaque categorie** et place le fichier dans le bon dossier
- `Move-Item` → Deplace le fichier vers `$destination`

---

#### **8. Ajout du nombre de fichiers dans le nom des dossiers**

```powershell
foreach ($category in $folders.Keys) {
    $folderPath = $folders[$category]
    $count = (Get-ChildItem -Path $folderPath -File).Count
    if ($count -gt 0) {
        Rename-Item -Path $folderPath -NewName "$folderPath ($count)" -Force
    }
}
```

- **Compte les fichiers** dans chaque dossier
- Renomme le dossier avec **le nombre de fichiers**

---

#### **9. Creation de l'archive ZIP**

```powershell
$date = Get-Date -Format "yyyy-MM-dd_HH-mm-ss"
$zipFile = "$sourceFolder\Archive_$date.zip"
Compress-Archive -Path "$archiveFolder\*" -DestinationPath $zipFile -Force
```

- Genere la date au format `YYYY-MM-DD_HH-mm-ss`
- `Compress-Archive` → **Cree une archive ZIP** contenant tout le dossier `Archive`

---

#### **10. Verification de la cle USB et copie de l'archive**

```powershell
$usbDrive = Get-PSDrive -PSProvider FileSystem | Where-Object { $_.Root -match "^[D-Z]:\\" }
```

- `Get-PSDrive` → Liste les **lecteurs disponibles**
- Filtre ceux **entre D: et Z:** (generalement **une cle USB**)

```powershell
if ($usbDrive) {
    $usbPath = "$($usbDrive.Root)\$([System.IO.Path]::GetFileName($zipFile))"
    Copy-Item -Path $zipFile -Destination $usbPath -Force
    Write-Host "Archive copiee sur la cle USB : $usbPath" -ForegroundColor Cyan
} else {
    Write-Host "Aucune cle USB detectee." -ForegroundColor Yellow
}
```

- **Si une cle USB est detectee**, copie l'archive dessus
- Affiche un message de confirmation

---

## ✍️ Rédigé par _Yulian_
