function varargout = gui_sample1(varargin)
% GUI_SAMPLE1 MATLAB code for gui_sample1.fig
%      GUI_SAMPLE1, by itself, creates a new GUI_SAMPLE1 or raises the existing
%      singleton*.
%
%      H = GUI_SAMPLE1 returns the handle to a new GUI_SAMPLE1 or the handle to
%      the existing singleton*.
%
%      GUI_SAMPLE1('CALLBACK',hObject,eventData,handles,...) calls the local
%      function named CALLBACK in GUI_SAMPLE1.M with the given input arguments.
%
%      GUI_SAMPLE1('Property','Value',...) creates a new GUI_SAMPLE1 or raises the
%      existing singleton*.  Starting from the left, property value pairs are
%      applied to the GUI before gui_sample1_OpeningFcn gets called.  An
%      unrecognized property name or invalid value makes property application
%      stop.  All inputs are passed to gui_sample1_OpeningFcn via varargin.
%
%      *See GUI Options on GUIDE's Tools menu.  Choose "GUI allows only one
%      instance to run (singleton)".
%
% See also: GUIDE, GUIDATA, GUIHANDLES

% Edit the above text to modify the response to help gui_sample1

% Last Modified by GUIDE v2.5 25-Oct-2016 19:45:12

% Begin initialization code - DO NOT EDIT
gui_Singleton = 1;
gui_State = struct('gui_Name',       mfilename, ...
                   'gui_Singleton',  gui_Singleton, ...
                   'gui_OpeningFcn', @gui_sample1_OpeningFcn, ...
                   'gui_OutputFcn',  @gui_sample1_OutputFcn, ...
                   'gui_LayoutFcn',  [] , ...
                   'gui_Callback',   []);
if nargin && ischar(varargin{1})
    gui_State.gui_Callback = str2func(varargin{1});
end

if nargout
    [varargout{1:nargout}] = gui_mainfcn(gui_State, varargin{:});
else
    gui_mainfcn(gui_State, varargin{:});
end
% End initialization code - DO NOT EDIT


% --- Executes just before gui_sample1 is made visible.
function gui_sample1_OpeningFcn(hObject, eventdata, handles, varargin)
% This function has no output args, see OutputFcn.
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% varargin   command line arguments to gui_sample1 (see VARARGIN)

% Choose default command line output for gui_sample1
handles.output = hObject;

% Update handles structure
guidata(hObject, handles);

% UIWAIT makes gui_sample1 wait for user response (see UIRESUME)
% uiwait(handles.figure1);


% --- Outputs from this function are returned to the command line.
function varargout = gui_sample1_OutputFcn(hObject, eventdata, handles) 
% varargout  cell array for returning output args (see VARARGOUT);
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Get default command line output from handles structure
%varargout{1} = handles.output;


% --- Executes on button press in browse.
function browse_Callback(hObject, eventdata, handles)
% hObject    handle to browse (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
global lc1
[file, pathname]=uigetfile({'*.jpg';'*.jpeg';'*.bmp';'*.gif';'*.png';'*.tif';'*.tiff';},'File Selector');
lc1=imread(strcat(pathname,file));
axes(handles.input_image);
imshow(lc1);

%individual band extraction
global red;
global green;
global blue;
global o_max;
global o_min;
global mean_r;
global mean_g;
global mean_b;
global std_dev_red;
global std_dev_green;
global std_dev_blue;
global s;
global s_g;
global s_b;
red=lc1(:,:,1);
green=lc1(:,:,2);
blue=lc1(:,:,3);
[row col band]=size(lc1);

o_max=255;
o_min=0;

red=double(red);
green=double(green);
blue=double(blue);

%standard deviation for red
sum_r=0.0;
sdr=0.0;
sum_r=sum(sum(red));
mean_r=sum_r/(row*col);
sdr=(red-mean_r).^2;
s=sum(sum(sdr));
std_dev_red=(sqrt(s/((row*col)-1)));


%standard deviation for green
sum_g=0;
sdg=0;
sum_g=sum(sum(green));
mean_g=sum_g/(row*col);
sdg=(green-mean_g).^2;
s_g=sum(sum(sdg));
std_dev_green=(sqrt(s_g/((row*col)-1)));


%standard deviation for blue
sum_b=0;
sdb=0;
sum_b=sum(sum(blue));
mean_b=sum_b/(row*col);
sdb=(blue-mean_b).^2;
s_b=sum(sum(sdb));
std_dev_blue=(sqrt(s_b/((row*col)-1)));



function input_k_Callback(hObject, eventdata, handles)
% hObject    handle to input_k (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of input_k as text
%        str2double(get(hObject,'String')) returns contents of input_k as a double

% --- Executes during object creation, after setting all properties.

function input_k_CreateFcn(hObject, eventdata, handles)
% hObject    handle to input_k (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



% --- Executes on button press in pushbutton2.
function pushbutton2_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
global k;
global i_min;
global i_max;
global i_min_b;
global i_max_b;
global i_max_g;
global i_min_g;
global std_dev_red;
global std_dev_green;
global std_dev_blue;
global mean_r;
global mean_g;
global mean_b;

k=str2double(get(handles.input_k,'String'));

%i_min and i_max for all bands
i_max=mean_r+(k*std_dev_red);
i_min=mean_r-(k*std_dev_red);
i_max_g=mean_g+(k*std_dev_green);
i_min_g=mean_g-(k*std_dev_green);
i_max_b=mean_b+(k*std_dev_blue);
i_min_b=mean_b-(k*std_dev_blue);

if (gt(i_max,255) ||  gt(i_max_g,255) || gt(i_max_b,255) || (i_min>255) || (i_min_g>255) || (i_min_b>255))
      errordlg('value of k out of range,please enter again.');
     
elseif (lt(i_min,0) || lt(i_min_g,0) || lt(i_min_b,0) || (i_max<0) || (i_max_g<0) || (i_max_b<0))
       errordlg('value of k out of range, please enter again.');
end


% --- Executes on button press in pushbutton3.
function pushbutton3_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton3 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
set(handles.input_k,'String','');

% --- Executes on button press in pushbutton4.
function pushbutton4_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton4 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
global k;
global o_max;
global o_min;
global i_min;
global i_max;
global i_min_b;
global i_max_b;
global i_max_g;
global i_min_g;
global red;
global green;
global blue;
global row;
global col;
global lc1;
global new_r;
global new_g;
global new_b;
global new_image;
new_r=zeros(row,col);
new_g=zeros(row,col);
new_b=zeros(row,col);

%contrast enhancement for red
slope_r=(o_max-o_min)/(i_max-i_min);
new_r=(red-i_min)*slope_r;
new_r=uint8(new_r);

%contrast enhancement for green
slope_g=(o_max-o_min)/(i_max_g-i_min_g);
new_g=(green-i_min_g)*slope_g;
new_g=uint8(new_g);

 
%contrast enhancement for blue
slope_b=(o_max-o_min)/(i_max_b-i_min_b);
new_b=(blue-i_min_b)*slope_b;
new_b=uint8(new_b);

%final image
new_image=cat(3,new_r,new_g,new_b);
axes(handles.axes2);
imshow(new_image);




% --- Executes on button press in pushbutton7.
function pushbutton7_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton7 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

%display histogram
global new_image;
global lc1;
axes(handles.axes4);
new_image=rgb2gray(new_image);
imhist(new_image);

axes(handles.axes3);
lc1=rgb2gray(lc1);
imhist(lc1);


% --- Executes on button press in pushbutton9.
function pushbutton9_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton9 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

%display individual bands
global new_r;
global new_g;
global new_b;
figure,imshow(new_r);
figure,imshow(new_g);
figure,imshow(new_b);


% --- Executes on button press in pushbutton11.
function pushbutton11_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton11 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
%saves output image in current folder
global new_image;
imwrite(new_image,'outputImage.jpg'); 
